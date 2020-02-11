---
title: sql_logins (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 01/20/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sql_logins_TSQL
- sql_logins_TSQL
- sys.sql_logins
- sql_logins
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sql_logins catalog view
ms.assetid: 0d9c5b09-86fe-40ff-baab-00b7c051402f
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 362ccc5c85523b3d37cb792a42e8be4cd87d7510
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68109001"
---
# <a name="syssql_logins-transact-sql"></a>sql_logins (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-pdw-md.md)]

  
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authentication ログインごとに 1 行のデータが返ります。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**\<継承された列>**|--|**Server_principals**から継承します。|  
|**is_policy_checked**|**bit**|パスワードポリシーが確認されます。|  
|**is_expiration_checked**|**bit**|パスワードの有効期限が確認されます。|  
|**password_hash**|**varbinary (256)**|SQL ログインパスワードのハッシュ。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降では、保存されたパスワード情報は salt 化パスワードの SHA-512 を使用して計算されます。|  
  
 このビューが継承する列の一覧については、「 [sys. server_principals &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)」を参照してください。  
  
## <a name="remarks"></a>解説  
 認証ログインと[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows 認証ログインの両方を表示するには、「 [sys. server_principals &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)」を参照してください。  
  
 包含データベースユーザーが有効になっている場合、ログインなしで接続を行うことができます。 これらのアカウントを識別するには、「 [sys. database_principals &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)」を参照してください。  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証ログインでは、独自のログイン名と sa ログインを参照できます。 他のログインを表示するには、ALTER ANY LOGIN、またはログインに対する権限が必要です。  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]詳細については、「[メタデータ表示の構成](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [セキュリティカタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [パスワードポリシー](../../relational-databases/security/password-policy.md)   
 [プリンシパル &#40;データベースエンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
