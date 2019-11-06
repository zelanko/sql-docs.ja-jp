---
title: Always Encrypted ウイザード | Microsoft Docs
ms.custom: ''
ms.date: 05/04/2016
ms.prod: sql
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql13.swb.alwaysencryptedwizard.encryption.f1
- sql13.swb.alwaysencryptedwizard.f1
- sql.swb.alwaysencryptedwizard.masterkey.f1
helpviewer_keywords:
- Wizard, Always Encrypted
ms.assetid: 68daddc9-ce48-49aa-917f-6dec86ad5af5
author: aliceku
ms.author: aliceku
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e45ddec1a380ea6ea867fb0306cca4176786fbf8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68043158"
---
# <a name="always-encrypted-wizard"></a>Always Encrypted ウイザード
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

**Always Encrypted ウイザード** を利用すれば、SQL Server データベースに保存されている機密データを保護できます。 Always Encrypted を使用すると、クライアントは SQL Server に暗号化キーを開示することなく、クライアント アプリケーション内の機密データを暗号化することができます。 結果として、Always Encrypted は、データを所有 (および表示できる) 人とデータを管理する (ただし、アクセス権を与えない) 人を分離します。  機能の詳細については、「 [Always Encrypted &#40;データベース エンジン&#41;](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)」を参照してください。  
 
 - ウィザードを使用して Always Encrypted を構成し、それをクライアント アプリケーションで使用する方法を説明したエンドツーエンド チュートリアルについては、[SQL Database チュートリアル:Always Encrypted を使用した機密データの保護](https://azure.microsoft.com/documentation/articles/sql-database-always-encrypted/)に関するページをご覧ください。  
 
 - ウィザードの利用方法を含む動画が必要な場合、「 [Keeping Sensitive Data Secure with Always Encrypted (Always Encrypted で機密データを守る)](https://channel9.msdn.com/events/DataDriven/SQLServer2016/AlwaysEncrypted)」をご覧ください。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] セキュリティ チームのブログ「 [SSMS Encryption Wizard - Enabling Always Encrypted in a Few Easy Steps](https://blogs.msdn.com/b/sqlsecurity/archive/2015/11/01/ssms-encryption-wizard-enabling-always-encrypted-made-easy.aspx)」(SSMS 暗号化ウィザード - 数回の手順で Always Encrypted を有効にする) も参照してください。  
 
 - **権限:** 暗号化された列に対してこのウィザードを使用してクエリを実行し、キーを選択するには、`VIEW ANY COLUMN MASTER KEY DEFINITION` 権限と `VIEW ANY COLUMN ENCRYPTION KEY DEFINITION` 権限が必要です。 新しいキーを作成するには、 `ALTER ANY COLUMN MASTER KEY` 権限と `ALTER ANY COLUMN ENCRYPTION KEY` 権限も必要です。  
 
 #### <a name="to-open-the-always-encrypted-wizard"></a>Always Encrypted ウイザード を開く
 
 1.  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のオブジェクト エクスプローラー コンポーネントで [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]に接続します。  
   
 2.  データベースを右クリックして **[タスク]** をポイントし、 **[列の暗号化]** をクリックします。  
   
 ## <a name="column-selection-page"></a>列の選択ページ
 - テーブルと列を見つけ、選択した列の暗号化の種類 (決定性またはランダム) と暗号化鍵を選択します。 現在暗号化されている列の暗号化を解除するには、 **[プレーン テキスト]** を選択します。 列の暗号化鍵を回転させるには、別の暗号化鍵を選択します。ウィザードが列の暗号化を解除し、新しい鍵で列を再び暗号化します。 (テンポラル テーブルとインメモリ テーブルの暗号化は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] でサポートされていますが、このウィザードでは構成できません。)  
 
## <a name="master-key-configuration-page"></a>マスター キーの構成ページ  
 - Windows 証明書ストアまたは Azure Key Vault で列の新しいマスター キーを作成します。 詳細については、「キー ストレージ」以下のリンクを参照してください。  
 
 - [列の選択] ページで列の暗号化鍵の自動生成を選択した場合、列に生成された暗号化鍵を暗号化する列のマスター キーを設定する必要があります。 列のマスター キーが既にデータベースに定義されている場合、それを選択できます。 (既存のマスター キーを使用するには、その鍵にアクセスするための権限が必要になります。)あるいは、選択したキー ストア (Windows 証明書ストアまたは Azure Key Vault) で列のマスター キーを生成し、そのキーをデータベースで定義できます。  
 
 ### <a name="key-storage"></a>**キー ストレージ**  
 
 - 列のマスター キーの格納場所を選択します。  
 
   - **Windows cert にマスター キーを保存** 詳細については、「 [Using Certificate Stores (証明書ストアの使用)](/windows/desktop/SecCrypto/using-certificate-stores)  
 
   - **AKV (Azure Key Vault) にマスター キーを保存** 詳細については、「 [Azure Key Vault の使用を開始する](https://azure.microsoft.com/documentation/articles/key-vault-get-started/)」を参照してください。  
 
 - Azure Key Vault で列のマスター キーを生成するには、Key Vault の **WrapKey**、 **UnwrapKey**、 **Verify**、 **Sign** 権限が必要になります。 **Get**、 **List**、 **Create**、 **Delete**、 **Update**、 **Import**、 **Backup**、 **Restore** 権限も場合によっては必要になります。 詳しくは、「[Azure Key Vault とは](https://azure.microsoft.com/documentation/articles/key-vault-whatis/)」および「[Set-AzKeyVaultAccessPolicy](/powershell/module/az.keyvault/set-azkeyvaultaccesspolicy)」をご覧ください。  
 
 - ウィザードでは 2 つのオプションのみがサポートされました。 ハードウェア セキュリティ モジュールとカスタマー ストアを [CREATE COLUMN MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/create-column-master-key-transact-sql.md)[!INCLUDE[tsql](../../../includes/tsql-md.md)] で構成する必要があります。  
 
 ## <a name="always-encrypted-terms"></a>Always Encrypted 用語  
 
 - **確定的な暗号化** は常に任意のプレーン テキストを指定した値の場合は、同じ暗号化された値を生成するメソッドを使用します。 明確な暗号化では、暗号化された値に基づくグループ化、等値によるフィルター処理、テーブル結合が可能ですが、暗号化されている列のパターンを調べることて、無許可のユーザーが暗号化されている値を推測できます。 暗号化されている値が True/False や North/South/East/West リージョンのような小さな集合である場合は、脆弱性が上がります。 明確な暗号化では、バイナリ 2 文字型の列の並べ替え順序を持つ列の照合順序を使用する必要があります。  
 
 - **暗号化をランダム化** は低い予測可能な方法でデータを暗号化するためのメソッドを使用します。 暗号のランダム化は安全性が上がりますが、暗号化する列で同等性による検索、グループ化、インデックス作成、結合ができなくなります。  

 - **列のマスター キー** は、列の暗号化鍵の暗号化に使用される保護鍵です。 列のマスター キーは信頼できる鍵の保管場所に保管する必要があります。 場所など、列のマスター キーに関する情報はシステム カタログ ビューのデータベースに保管されます。  

 - **列の暗号化鍵** は、データベース列に保存されている機密データの暗号化に使用されます。 列のすべての値を 1 つの列暗号化鍵で暗号化できます。 列暗号化鍵の暗号化された値は、システム カタログ ビューでデータベースに保存されます。 列の暗号化キーは、バックアップとして安全で信頼できる場所に格納する必要があります。  

 ## <a name="see-also"></a>参照  
 - [Always Encrypted &#40;データベース エンジン&#41;](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 - [Azure Key Vault を使用する拡張キー管理 &#40;SQL Server&#41;](../../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)  
