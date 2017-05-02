---
title: "Always Encrypted による暗号化 | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 02/29/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Always Encrypted, cryptography system
ms.assetid: ae8226ff-0853-4716-be7b-673ce77dd370
caps.latest.revision: 11
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ee5419dc374c545daa1249f2e6f76d8d13ac4695
ms.lasthandoff: 04/11/2017

---
# <a name="always-encrypted-cryptography"></a>Always Encrypted による暗号化
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  このドキュメントでは、 [および](../../../relational-databases/security/encryption/always-encrypted-database-engine.md) において、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Always Encrypted [!INCLUDE[ssSDSFull](../../../includes/sssdsfull-md.md)]機能で使用される暗号化マテリアルを派生させる暗号化アルゴリズムとメカニズムについて説明します。  
  
## <a name="keys-key-stores-and-key-encryption-algorithms"></a>キー、キー ストアおよびキーの暗号化アルゴリズム  
 Always Encrypted では、列マスター キーと列暗号化キーという 2 種類のキーを使用します。  
  
 列マスター キー (CMK) は、常にクライアントに制御され、外部キー ストアに格納されているキーの暗号化キー (つまり、他のキーの暗号化に使用されるキー) です。 Always Encrypted が有効なクライアント ドライバーは CMK ストア プロバイダーを介してキー ストアと対話します。このプロバイダーはドライバー ライブラリの一部 ( [!INCLUDE[msCoName](../../../includes/msconame-md.md)]/system プロバイダー) またはクライアント アプリケーションの一部 (カスタム プロバイダー) である場合があります。 現在、クライアント ドライバー ライブラリには、[Windows 証明書ストア](https://msdn.microsoft.com/library/windows/desktop/aa388160)およびハードウェア セキュリティ モジュール (HSM) の [!INCLUDE[msCoName](../../../includes/msconame-md.md)] キー ストア プロバイダーが含まれています。  (現在のプロバイダーの一覧については、「[CREATE COLUMN MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/create-column-master-key-transact-sql.md)」を参照してください)。アプリケーション開発者は、任意のストアのカスタム プロバイダーを提供できます。  
  
 列暗号化キー (CEK) は、CMK によって保護されているコンテンツ暗号化キー (つまり、データを保護するために使用されるキー) です。  
  
 すべての [!INCLUDE[msCoName](../../../includes/msconame-md.md)] CMK ストア プロバイダーは、セクション A.2.1 の RFC 3447 で指定されている既定のパラメーターを指定し、RSA-OAEP (RSA with Optimal Asymmetric Encryption Padding) を使用して CEK を暗号化します。 これらの既定のパラメーターでは、SHA-1 のハッシュ関数と、SHA-1 を指定した MGF1 のマスク生成関数を使用します。  
  
## <a name="data-encryption-algorithm"></a>データ暗号化のアルゴリズム  
 Always Encrypted では **AEAD_AES_256_CBC_HMAC_SHA_256** アルゴリズムを使用して、データベース内のデータを暗号化します。  
  
 **AEAD_AES_256_CBC_HMAC_SHA_256** は、 [http://tools.ietf.org/html/draft-mcgrew-aead-aes-cbc-hmac-sha2-05](http://tools.ietf.org/html/draft-mcgrew-aead-aes-cbc-hmac-sha2-05)の仕様ドラフトから派生しています。 このアルゴリズムでは、Encrypt-then-MAC 手法に従って、関連データで認証済み暗号化スキームを使用します。 つまり、プレーンテキストが最初に暗号化され、その結果として生成される暗号化テキストに基づいて MAC が生成されます。  
  
 パターンを非表示にするために、 **AEAD_AES_256_CBC_HMAC_SHA_256** では暗号化ブロック チェーン (CBC) という操作モードを使用します。この場合、初期値は初期化ベクター (IV) という名前のシステムに渡されます。 CBC モードの詳細については、 [http://csrc.nist.gov/publications/nistpubs/800-38a/sp800-38a.pdf](http://csrc.nist.gov/publications/nistpubs/800-38a/sp800-38a.pdf)を参照してください。  
  
 **AEAD_AES_256_CBC_HMAC_SHA_256** は、以下の手順を使用して指定されたプレーンテキストの暗号化テキストの値を計算します。  
  
### <a name="step-1-generating-the-initialization-vector-iv"></a>手順 1: 初期化ベクター (IV) の生成  
 Always Encrypted では、以下の 2 種類の **AEAD_AES_256_CBC_HMAC_SHA_256**がサポートされています。  
  
-   ランダム化  
  
-   決定的  
  
 ランダムな暗号化の場合、IV はランダムに生成されます。 その結果、同じプレーンテキストが暗号化されるたびに、別の暗号化テキストが生成され、情報の漏えいを防ぐことができます。  
  
```  
When using randomized encryption: IV = Generate cryptographicaly random 128bits  
```  
  
 決定的な暗号化の場合、IV はランダムに生成されませんが、その代わりに、以下のアルゴリズムを使用してプレーンテキスト値から派生します。  
  
```  
When using deterministic encryption: IV = HMAC-SHA-256( iv_key, cell_data ) truncated to 128 bits.  
```  
  
 iv_key は以下の方法で CEK から派生します。  
  
```  
iv_key = HMAC-SHA-256(CEK, "Microsoft SQL Server cell IV key" + algorithm + CEK_length)  
```  
  
 HMAC 値の切り捨ては、IV での必要に応じて 1 つのデータ ブロックに収まるように実行されます。    
その結果、決定的な暗号化では常に指定されたプレーンテキスト値に対して同じ暗号化テキストが生成されます。これにより、2 つのプレーンテキスト値のそれぞれ対応する暗号化テキスト値を比較して、プレーンテキスト値が同じであるかどうかを推定できます。 この制限された情報の公開により、データベース システムは暗号化された列値の等価比較をサポートできます。  
  
 決定的な暗号化は、定義済みの IV 値を使用するなどして、パターンを非表示にする場合や代替との比較を行う場合により効果的です。  
  
### <a name="step-2-computing-aes256cbc-ciphertext"></a>手順 2: AES_256_CBC 暗号化テキストの計算  
 IV を計算した後、 **AES_256_CBC** 暗号化テキストが次のように生成されます。  
  
```  
aes_256_cbc_ciphertext = AES-CBC-256(enc_key, IV, cell_data) with PKCS7 padding.  
```  
  
 この暗号化キー (enc_key) は次のように CEK から派生します。  
  
```  
enc_key = HMAC-SHA-256(CEK, "Microsoft SQL Server cell encryption key" + algorithm + CEK_length )  
```  
  
### <a name="step-3-computing-mac"></a>手順 3: MAC の計算  
 その後、MAC は以下のアルゴリズムを使用して計算されます。  
  
```  
MAC = HMAC-SHA-256(mac_key, versionbyte + IV + Ciphertext + versionbyte_length)  
```  
  
 各要素の説明は次のとおりです。  
  
```  
versionbyte = 0x01 and versionbyte_length = 1   
mac_key = HMAC-SHA-256(CEK, "Microsoft SQL Server cell MAC key" + algorithm + CEK_length)  
```  
  
### <a name="step-4-concatenation"></a>手順 4: 連結  
 最後に、暗号化された値は、アルゴリズム バージョン バイト、MAC、IV および AES_256_CBC 暗号化テキストを単に連結して生成されます。  
  
```  
aead_aes_256_cbc_hmac_sha_256 = versionbyte + MAC + IV + aes_256_cbc_ciphertext  
```  
  
## <a name="ciphertext-length"></a>暗号化テキストの長さ  
 **AEAD_AES_256_CBC_HMAC_SHA_256** 暗号化テキストの各コンポーネントの長さ (バイト単位) は次のとおりです。  
  
-   versionbyte: 1  
  
-   MAC: 32  
  
-   IV: 16  
  
-   aes_256_cbc_ciphertext: `(FLOOR (DATALENGTH(cell_data)/ block_size) + 1)* block_size`。  
  
    -   block_size は 16 バイトです。  
  
    -   cell_data はプレーンテキスト値です。  
  
     したがって、aes_256_cbc_ciphertext の最小サイズは 1 ブロックは (16 バイト) になります。  
  
 指定されたプレーンテキスト値を暗号化した場合の暗号化テキストの長さは、以下の式を使用して計算できます。  
  
```  
1 + 32 + 16 + (FLOOR(DATALENGTH(cell_data)/16) + 1) * 16  
```  
  
 例:  
  
-   4 バイト長の **int** プレーンテキスト値は、暗号化後に 65 バイト長のバイナリ値になります。  
  
-   2,000 バイト長の **nchar(1000)** プレーンテキスト値は、暗号化後に 2,065 バイト長のバイナリ値になります。  
  
 次の表には、データ型と各型の暗号化テキストの長さの完全な一覧が含まれています。  
  
|データ型|暗号化テキストの長さ (バイト)|  
|---------------|---------------------------------|  
|**bigint**|65|  
|**[バイナリ]**|多様。 上の式を使用します。|  
|**bit**|65|  
|**char**|多様。 上の式を使用します。|  
|**date**|65|  
|**datetime**|65|  
|**datetime2**|65|  
|**datetimeoffset**|65|  
|**decimal**|81|  
|**float**|65|  
|**geography**|該当なし (サポートされていません)|  
|**geometry**|該当なし (サポートされていません)|  
|**hierarchyid**|該当なし (サポートされていません)|  
|**image**|該当なし (サポートされていません)|  
|**int**|65|  
|**money**|65|  
|**nchar**|多様。 上の式を使用します。|  
|**ntext**|該当なし (サポートされていません)|  
|**numeric**|81|  
|**nvarchar**|多様。 上の式を使用します。|  
|**real**|65|  
|**smalldatetime**|65|  
|**smallint**|65|  
|**smallmoney**|65|  
|**sql_variant**|該当なし (サポートされていません)|  
|**sysname**|該当なし (サポートされていません)|  
|**text**|該当なし (サポートされていません)|  
|**time**|65|  
|**timestamp**<br /><br /> (**rowversion**)|該当なし (サポートされていません)|  
|**tinyint**|65|  
|**uniqueidentifier**|81|  
|**varbinary**|多様。 上の式を使用します。|  
|**varchar**|多様。 上の式を使用します。|  
|**xml**|該当なし (サポートされていません)|  
  
## <a name="net-reference"></a>.NET リファレンス  
 このドキュメントに記載されているアルゴリズムの詳細については、 **.NET リファレンス** の **SqlAeadAes256CbcHmac256Algorithm.cs** ファイルと [SqlColumnEncryptionCertificateStoreProvider.cs](http://referencesource.microsoft.com/)ファイルを参照してください。  
  
## <a name="see-also"></a>参照  
 [Always Encrypted &#40;データベース エンジン&#41;](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 [Always Encrypted &#40;クライアント開発&#41;](../../../relational-databases/security/encryption/always-encrypted-client-development.md)  
  
  

