---
title: TRUSTWORTHY データベース プロパティ | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: security
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- TRUSTWORTHY database property
ms.assetid: 64b2a53d-4416-4a19-acc0-664a61b45348
caps.latest.revision: 22
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 0a2a364b8d01d5a56c1d28464084ca26149de8d8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="trustworthy-database-property"></a>TRUSTWORTHY データベース プロパティ
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  TRUSTWORTHY データベース プロパティを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスがデータベースとその内容を信頼するかどうかを示します。 この設定は既定では OFF ですが、ALTER DATABASE ステートメントを使用して ON に設定できます。 たとえば、 `ALTER DATABASE AdventureWorks2012 SET TRUSTWORTHY ON;`のようにします。  
  
> [!NOTE]  
>  このオプションを設定するには、 **sysadmin** 固定サーバー ロールのメンバーである必要があります。  
  
 このプロパティを使用することで、次のようなオブジェクトの 1 つが含まれているデータベースをアタッチすることによって生じる特定の脅威を軽減できます。  
  
-   EXTERNAL_ACCESS 権限または UNSAFE 権限が設定された、悪意のあるアセンブリ。 詳細については、「 [CLR 統合のセキュリティ](../../relational-databases/clr-integration/security/clr-integration-security.md)」を参照してください。  
  
-   高い特権を所持するユーザーとして実行するように定義された悪意のあるモジュール。 詳細については、「[EXECUTE AS 句 &#40;Transact-SQL&#41;](../../t-sql/statements/execute-as-clause-transact-sql.md)」を参照してください。  
  
 どちらの状況でもある程度の特権が必要になり、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに既にアタッチされているデータベースのコンテキストで使用されるときは、適切なメカニズムによって保護されます。 しかし、データベースがオフラインであれば、データベース ファイルへのアクセス権のあるユーザーは、選択した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにデータベースをアタッチし、悪意のあるコンテンツをデータベースに追加できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]でデータベースがデタッチされ、再アタッチされると、データベース ファイルへのアクセスを制限する特定の権限が、データ ファイルとログ ファイルに設定されます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにアタッチされるデータベースはすぐには信頼できないので、データベースが信頼できるものとして明示的に設定されるまでは、データベースはデータベースのスコープを超えてリソースにアクセスすることはできません。 また、データベース外のリソースにアクセスするように設計されているモジュール、および EXTERNAL_ACCESS 権限と UNSAFE 権限のいずれかが設定されているアセンブリを正常に実行するには、追加の要件が課せられます。  
  
## <a name="related-content"></a>関連コンテンツ  
 [SQL Server データベース エンジンと Azure SQL Database のセキュリティ センター](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)  
  
  
