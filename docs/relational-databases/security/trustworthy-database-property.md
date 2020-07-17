---
title: TRUSTWORTHY データベース プロパティ | Microsoft Docs
description: TRUSTWORTHY データベース プロパティについて説明します。これは、SQL Server のインスタンスがデータベースとその内容を信頼するかどうかを示します。 既定値は OFF です。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: security
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- TRUSTWORTHY database property
ms.assetid: 64b2a53d-4416-4a19-acc0-664a61b45348
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 4db2515c51085e79d67e6ace4cbbe1abedc91023
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85736960"
---
# <a name="trustworthy-database-property"></a>TRUSTWORTHY データベース プロパティ
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  TRUSTWORTHY データベース プロパティを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスがデータベースとその内容を信頼するかどうかを示します。 この設定は既定では OFF ですが、ALTER DATABASE ステートメントを使用して ON に設定できます。 たとえば、「 `ALTER DATABASE AdventureWorks2012 SET TRUSTWORTHY ON;` 」のように入力します。  
  
> [!NOTE]  
>  このオプションを設定するには、 **sysadmin** 固定サーバー ロールのメンバーである必要があります。  
  
 このプロパティを使用することで、次のようなオブジェクトの 1 つが含まれているデータベースをアタッチすることによって生じる特定の脅威を軽減できます。  
  
-   EXTERNAL_ACCESS 権限または UNSAFE 権限が設定された、悪意のあるアセンブリ。 詳細については、「 [CLR 統合のセキュリティ](../../relational-databases/clr-integration/security/clr-integration-security.md)」を参照してください。  
  
-   高い特権を所持するユーザーとして実行するように定義された悪意のあるモジュール。 詳細については、「[EXECUTE AS 句 &#40;Transact-SQL&#41;](../../t-sql/statements/execute-as-clause-transact-sql.md)」を参照してください。  
  
 どちらの状況でもある程度の特権が必要になり、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに既にアタッチされているデータベースのコンテキストで使用されるときは、適切なメカニズムによって保護されます。 しかし、データベースがオフラインであれば、データベース ファイルへのアクセス権のあるユーザーは、選択した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにデータベースをアタッチし、悪意のあるコンテンツをデータベースに追加できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]でデータベースがデタッチされ、再アタッチされると、データベース ファイルへのアクセスを制限する特定の権限が、データ ファイルとログ ファイルに設定されます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにアタッチされるデータベースはすぐには信頼できないので、データベースが信頼できるものとして明示的に設定されるまでは、データベースはデータベースのスコープを超えてリソースにアクセスすることはできません。 そのため、TRUSTWORTHY オプションをオンにしているデータベースをバックアップするか、デタッチするとき、同じか別の SQL Server インスタンスにそのデータベースをアタッチまたは復元する場合、アタッチ/復元の完了時に TRUSTWORTHY プロパティがオフに設定されます。 また、データベース外のリソースにアクセスするように設計されているモジュール、および EXTERNAL_ACCESS 権限と UNSAFE 権限のいずれかが設定されているアセンブリを正常に実行するには、追加の要件が課せられます。  
  
## <a name="related-content"></a>関連コンテンツ  
 [SQL Server データベース エンジンと Azure SQL Database のセキュリティ センター](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)  
  
  
