---
title: "MASTER KEY (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_MASTER_KEY_TSQL
- MASTER_KEY_TSQL
- MASTER KEY
- CREATE MASTER KEY
dev_langs:
- TSQL
helpviewer_keywords:
- encryption [SQL Server], Database Master Key
- database master key [SQL Server]
- CREATE MASTER KEY statement
- cryptography [SQL Server], Database Master Key
- database master key [SQL Server], creating
ms.assetid: 1710a305-1a4f-48ec-836c-11ffd0356d76
caps.latest.revision: 50
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e051e59ebae464942068521a95a1d5b06389304e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-master-key-transact-sql"></a>CREATE MASTER KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  データベース マスター キーを作成します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server and Parallel Data Warehouse  
  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'password'  
[ ; ]  
```  
  
```  
-- Syntax for Azure SQL Database and Azure SQL Data Warehouse  
  
CREATE MASTER KEY [ ENCRYPTION BY PASSWORD ='password' ]
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 パスワード ='*パスワード*'  
 データベース内のマスター キーの暗号化に使用されているパスワードを指定します。 *パスワード*のインスタンスを実行しているコンピューターの Windows パスワード ポリシーの要件を満たす必要がある[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 *パスワード*が省略可能で[!INCLUDE[ssSDS](../../includes/sssds-md.md)]と[!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)]です。  
  
## <a name="remarks"></a>解説  
 データベース マスター キーは対称キーで、証明書の秘密キーやデータベース内に存在する非対称キーを保護するときに使用します。 データベース マスター キーを作成するときには、AES_256 アルゴリズムとユーザー指定のパスワードを使用してマスター キーを暗号化します。 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]と[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、トリプル DES アルゴリズムを使用します。 マスター キーの暗号化を自動的に解除できるようにするには、サービス マスター キーを使用してキーのコピーを暗号化し、データベースと master の両方に格納します。 通常、master に格納されたコピーは、マスター キーが変更されるたびに暗黙的に更新されます。 この既定の DROP ENCRYPTION BY SERVICE MASTER KEY オプションを使用して変更できます[ALTER MASTER KEY](../../t-sql/statements/alter-master-key-transact-sql.md)です。 使用して、サービス マスター _ キーによって暗号化されていないマスター _ キーを開く必要があります、 [OPEN MASTER KEY](../../t-sql/statements/open-master-key-transact-sql.md)ステートメントとパスワード。  
  
 master 内の sys.databases カタログ ビューの is_master_key_encrypted_by_server 列には、データベース マスター キーがサービス マスター キーによって暗号化されているかどうかが示されます。  
  
 データベース マスター キーに関する情報は、sys.symmetric_keys カタログ ビューで確認できます。  

SQL Server と Parallel Data Warehouse では、マスター _ キー通常およびにより保護されて、サービス マスター _ キーには、少なくとも 1 つのパスワード。 別のサーバー (ログ配布を復元するバックアップなど) に物理的に移動されているデータベースが発生した場合、データベースにが含まれます (この暗号化を使用して明示的に削除された場合を除き、元のサーバー サービス マスター _ キーによって暗号化されたマスター_キーのコピーにはALTER MASTER KEY DDL)、および CREATE MASTER KEY または後続の ALTER MASTER KEY DDL 操作のいずれかの中に指定された各パスワードによって暗号化されたコピーです。 マスター_キー、およびデータベースを移動した後は、キーの階層ではルートとして、マスター _ キーを使用して暗号化されたすべてのデータを回復するために、ユーザーが、マスター _ キーを保護するためのパスワードのいずれかを使用して、OPEN MASTER KEY ステートメントを使用するか、、マスター _ キーのバックアップを復元または、新しいサーバーでは、元のサービス マスター _ キーのバックアップを復元します。 

[!INCLUDE[ssSDS](../../includes/sssds-md.md)]と[!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)]、パスワード保護と見なされないように、マスター _ キーのサービス マスター _ キーの保護は、データベースがの移動先 1 台のサーバーから別の状況でのデータ損失シナリオを防ぐために安全機構Microsoft Azure プラットフォームによって管理されます。 したがって、メーザ キーのパスワードは省略可能で[!INCLUDE[ssSDS](../../includes/sssds-md.md)]と[!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)]です。
  
> [!IMPORTANT]  
>  使用して、マスター _ キーをバックアップする必要があります[マスター _ キーのバックアップ](../../t-sql/statements/backup-master-key-transact-sql.md)し、オフサイトの安全な場所にバックアップを格納します。  
  
 サービス マスター キーとデータベース マスター キーは、AES-256 アルゴリズムを使用して保護されます。  
  
## <a name="permissions"></a>Permissions  
 データベースに対する CONTROL 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、現在のデータベースのデータベース マスター _ キーを作成します。 パスワードを使用して、キーを暗号化`23987hxJ#KL95234nl0zBe`です。  
  
```  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '23987hxJ#KL95234nl0zBe';  
GO  
```  

  
## <a name="see-also"></a>参照  
 [sys.symmetric_keys & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-symmetric-keys-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [MASTER KEY &#40; を開くTRANSACT-SQL と #41 です。](../../t-sql/statements/open-master-key-transact-sql.md)   
 [ALTER MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-master-key-transact-sql.md)   
 [DROP MASTER KEY & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-master-key-transact-sql.md)   
 [CLOSE MASTER KEY & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/close-master-key-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  



