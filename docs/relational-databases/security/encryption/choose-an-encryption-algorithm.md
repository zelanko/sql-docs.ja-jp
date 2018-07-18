---
title: 暗号化アルゴリズムの選択 | Microsoft Docs
ms.custom: ''
ms.date: 01/08/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: security
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- cryptography [SQL Server], algorithms
- encryption [SQL Server], algorithms
- security [SQL Server], encryption
- algorithms [SQL Server encryption]
ms.assetid: 8227028c-a9c9-489d-bd27-fbf8242634ae
author: aliceku
ms.author: aliceku
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 27ed854b8dc14c25979968b5ce9d3833fe0cef05
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37302862"
---
# <a name="choose-an-encryption-algorithm"></a>暗号化アルゴリズムの選択
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  暗号化は多層防御の 1 つであり、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のインスタンスに対するセキュリティ対策として利用することができます。  
  
 暗号化アルゴリズムによって定義されるデータ変換は、未承認ユーザーが容易に復元できないものです。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] DES、Triple DES、TRIPLE_DES_3KEY、RC2、RC4、128 ビット RC4、DESX、128 ビット AES、192 ビット AES、256 ビット AES など、複数のアルゴリズムがサポートされ、管理者および開発者が必要に応じて選択できるようになっています。  
  
> [!NOTE]  
>  [!INCLUDE[ssSQL15](../../../includes/sssql15-md.md)]以降、AES_128、AES_192、AES_256 以外のすべてのアルゴリズムが使用されなくなりました。 古いアルゴリズムを使用する場合は (推奨されません)、データベース互換性レベルを 120 以下に設定する必要があります。  
  
 理想的なアルゴリズムは状況によって異なります。また、個々のアルゴリズムの利点についても、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] オンライン ブックでは扱っていません。 ただし、一般論としては、次のような原則があります。  
  
-   通常、強力な暗号化では、弱い暗号化よりも多くの CPU リソースを消費します。  
  
-   通常、短いキーより長いキーの方が、強力な暗号化を行えます。  
  
-   非対称暗号化は、同じキー長を使用した対称暗号化よりも弱くなりますが、処理速度は比較的遅くなります。  
  
-   長いキーを使用したブロック暗号は、ストリーム暗号よりも強力です。  
  
-   長い複雑なパスワードは、短いパスワードよりも強力です。  
  
-   大量のデータを暗号化する場合は、対称キーを使用してデータを暗号化し、非対称キーを使用して対称キーを暗号化します。  
  
-   暗号化されたデータは圧縮できませんが、圧縮されたデータは暗号化できます。 圧縮を使用する場合、データを暗号化する前にデータを圧縮する必要があります。  
  
> [!IMPORTANT]  
>  RC4 アルゴリズムは、旧バージョンとの互換性のためにのみサポートされています。 データベース互換性レベルが 90 または 100 の場合、新しい素材は RC4 または RC4_128 を使用してのみ暗号化できます  (非推奨)。AES アルゴリズムのいずれかなど、新しいアルゴリズムを使用してください。 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 以降では、どの互換性レベルでも、RC4 または RC4_128 を使用して暗号化された素材を暗号化解除できます。  
>   
>  異なるデータ ブロックに対して同じ RC4 または RC4_128 KEY_GUID を繰り返し使用すると、同一の RC4 キーが生成されます。これは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] が自動的に salt を提供しないためです。 同一の RC4 キーを繰り返し使用することは、暗号強度を著しく低下させる周知の間違いです。 そのため、RC4 キーワードおよび RC4_128 キーワードは非推奨とされます。 [!INCLUDE[ssNoteDepFutureDontUse](../../../includes/ssnotedepfuturedontuse-md.md)]  
  
 暗号化アルゴリズムおよび暗号化テクノロジの詳細については、MSDN の『.NET Framework 開発者ガイド』で、「 [セキュリティの基本概念](http://go.microsoft.com/fwlink/?LinkId=62082) 」を参照してください。  
  
 **DES アルゴリズムに関する説明:**  
  
-   DESX は不適切な名前でした。 ALGORITHM = DESX を使用して作成された対称キーでは、実際には 192 ビット キーを使用した TRIPLE DES 暗号が使用されます。 DESX アルゴリズムは提供されません。 [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
-   ALGORITHM = TRIPLE_DES_3KEY を使用して作成された対称キーでは、192 ビット キーを使用した TRIPLE DES が使用されます。  
  
-   ALGORITHM = TRIPLE_DES を使用して作成された対称キーでは、128 ビット キーを使用した TRIPLE DES が使用されます。  
  
## <a name="related-tasks"></a>Related Tasks  
  
|||  
|-|-|  
|対称キーを使用する暗号化|[CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/create-symmetric-key-transact-sql.md)|  
|非対称キーを使用する暗号化|[CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/create-asymmetric-key-transact-sql.md)|  
|証明書を使用する暗号化|[CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../../t-sql/statements/create-certificate-transact-sql.md)|  
|透過的なデータ暗号化を使用するデータベース ファイルの暗号化|[透過的なデータ暗号化 &#40;TDE&#41;](../../../relational-databases/security/encryption/transparent-data-encryption.md)|  
|テーブルの 1 つの列を暗号化する方法|[データの列の暗号化](../../../relational-databases/security/encryption/encrypt-a-column-of-data.md)|  
  
## <a name="see-also"></a>参照  
 [SQL Server の暗号化](../../../relational-databases/security/encryption/sql-server-encryption.md)   
 [暗号化階層](../../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
