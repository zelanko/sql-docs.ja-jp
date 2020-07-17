---
title: Database Mail XPs サーバー構成オプション | Microsoft Docs
description: "\"DatabaseMail XPs\" オプションについて説明します。 このオプションをオンにして、SQL Server でデータベース メールを使用できるようにするさまざまな方法について説明します。"
ms.custom: ''
ms.date: 11/27/2018
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Database Mail XPs option
- Database Mail [SQL Server], enabling
ms.assetid: e22c4e63-1792-473b-af11-14a7931ca9ed
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 0d495017b9bf2a5f58a5a880f1ce9696976ebd50
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85772568"
---
# <a name="database-mail-xps-server-configuration-option"></a>Database Mail XPs サーバー構成オプション

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

**Database Mail XPs** オプションを使用して、サーバーのデータベース メールを有効にします。 指定できる値は、  
  
- `0`:データベース メールを使用できません (既定)。  
  
- `1`:データベース メールを使用できます。  
  
 この設定は、サーバーを停止して再起動しなくてもすぐに有効になります。  
  
 データベース メールを使用するには、データベース メールを有効にしてから、データベース メールのホスト データベースを構成する必要があります。  
  
 **データベース メール構成ウィザード**を使用してデータベース メールを構成すると、`msdb` データベースのデータベース メール拡張ストアド プロシージャが有効になります。 **データベース メール構成ウィザード**を使用する場合、以下の例の `sp_configure` を使用する必要はありません。  
  
 **Database Mail XPs** オプションを `0` に設定すると、データベース メールは開始されません。 データベース メールが実行されている場合にこのオプションを `0` に設定すると、`DatabaseMailExeMinimumLifeTime` オプションで設定したアイドル状態の時間が続くまで、データベース メールは継続して実行され、メールが送信されます。  
  
## <a name="examples"></a>例
 次の例では、データベース メール拡張ストアド プロシージャが有効になります。  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Database Mail XPs', 1;  
GO  
RECONFIGURE  
GO  
```  

次の例では、データベース メール拡張ストアド プロシージャがまだ有効ではない場合に有効になります。

```sql
IF EXISTS (
    SELECT 1 FROM sys.configurations 
    WHERE NAME = 'Database Mail XPs' AND VALUE = 0)
BEGIN
  PRINT 'Enabling Database Mail XPs'
  EXEC sp_configure 'show advanced options', 1;  
  RECONFIGURE
  EXEC sp_configure 'Database Mail XPs', 1;  
  RECONFIGURE  
END
```

## <a name="see-also"></a>参照
[データベース メール](../../relational-databases/database-mail/database-mail.md)  
