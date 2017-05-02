---
title: "[セキュリティ保護可能なリソース] | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 10/18/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.roleproperties.selectobject.f1
helpviewer_keywords:
- securables [SQL Server]
- schemas [SQL Server], securables
- database securables [SQL Server]
- hierarchies [SQL Server], securables
- server securables [SQL Server]
ms.assetid: bfa748f0-70b0-453c-870a-04b7b205b9ff
caps.latest.revision: 41
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 51db5d7a36569601e7d21d5fc50d16230b85ea5d
ms.lasthandoff: 04/11/2017

---
# <a name="securables"></a>[セキュリティ保護可能なリソース]
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  セキュリティ保護可能なリソースは、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] の承認システムによりアクセスが制限されたリソースです。 たとえば、テーブルはセキュリティ保護可能です。 セキュリティ保護可能なリソースの中には他のセキュリティ保護可能なリソースに含まれているものがあります。これらは "スコープ" と呼ばれ、それ自体をセキュリティで保護できる入れ子構造の階層を形成しています。 セキュリティ保護可能なスコープは、 **サーバー**、 **データベース**、および **スキーマ**です。  
  
## <a name="securable-scope-server"></a>セキュリティ保護可能なスコープ: サーバー  
 **サーバー** セキュリティ保護可能なスコープには、次のセキュリティ保護可能なリソースが含まれています。  
  
-   可用性グループ  
  
-   エンドポイント  
  
-   Login  
  
-   サーバー ロール  
  
-   データベース  
  
## <a name="securable-scope-database"></a>セキュリティ保護可能なスコープ: データベース  
 **データベース** セキュリティ保護可能なスコープには、次のセキュリティ保護可能なリソースが含まれています。  
  
-   アプリケーション ロール  
  
-   アセンブリ  
  
-   非対称キー  
  
-   Certificate  
  
-   コントラクト  
  
-   フルテキスト カタログ  
  
-   フルテキスト ストップリスト  
  
-   メッセージ型  
  
-   リモート サービス バインド  
  
-   (データベース) ロール  
  
-   Route  
  
-   スキーマ  
  
-   検索プロパティ リスト  
  
-   サービス  
  
-   対称キー  
  
-   ユーザー  
  
## <a name="securable-scope-schema"></a>セキュリティ保護可能なスコープ: スキーマ  
 **スキーマ** セキュリティ保護可能なスコープには、次のセキュリティ保護可能なリソースが含まれています。  
  
-   型  
  
-   XML スキーマ コレクション  
  
-   オブジェクト – オブジェクト クラスのメンバーは次のとおりです。  
  
    -   Aggregate  
  
    -   関数  
  
    -   手順  
  
    -   キュー  
  
    -   シノニム  
  
    -   テーブル  
  
    -   表示 
    
    -   外部テーブル 
  
## <a name="controlling-access-to-a-securable"></a>セキュリティ保護可能なものへのアクセスの制御  
 セキュリティ保護可能なものに対する権限を受け取るエンティティは、プリンシパルと呼ばれます。 最も一般的なプリンシパルは、ログインとデータベース ユーザーです。 セキュリティ保護可能なものへのアクセスは、権限を許可または拒否することや、アクセスが可能なロールにログインおよびユーザーを追加することによって制御されます。 アクセス許可を制御する方法の詳細については、「[GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)」、「[REVOKE &#40;Transact-SQL&#41;](../../t-sql/statements/revoke-transact-sql.md)」、「[DENY &#40;Transact-SQL&#41;](../../t-sql/statements/deny-transact-sql.md)」、「[sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)」および「[sp_droprolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md)」を参照してください。  
  
> [!CAUTION]  
>  セットアップ時にシステム オブジェクトに付与された既定のアクセス許可は、発生する可能性のある脅威に対して慎重に評価されているため、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストールの際、セキュリティ強化の一部として変更する必要はありません。 システム オブジェクトのアクセス許可の変更はどのようなものであっても、機能を制限または中断する可能性があり、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストールがサポートされていない状態のままになる場合があります。  
  
## <a name="related-content"></a>関連コンテンツ  
 [データベース エンジンの権限の概要](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)  
  
 [SQL Server の保護](../../relational-databases/security/securing-sql-server.md)  
  
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)  
  
 [sys.database_role_members &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md)  
  
 [sys.server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)  
  
 [sys.server_role_members &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md)  
  
 [sys.sql_logins &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-logins-transact-sql.md)  
  
  

