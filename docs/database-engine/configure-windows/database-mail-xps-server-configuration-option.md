---
title: Database Mail XPs サーバー構成オプション | Microsoft Docs
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
author: MikeRayMSFT
ms.author: mikeray
manager: jroth
ms.openlocfilehash: f350a5027957acba7e9e8689b8650bb545368030
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66767917"
---
# <a name="database-mail-xps-server-configuration-option"></a>Database Mail XPs サーバー構成オプション

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

**Database Mail XPs** オプションを使用して、サーバーのデータベース メールを有効にします。 可能な値は次のとおりです。  
  
- `0`:データベース メールを使用できません (既定)。  
  
- `1`:データベース メールを使用できます。  
  
 この設定は、サーバーを停止して再起動しなくてもすぐに有効になります。  
  
 データベース メールを使用するには、データベース メールを有効にしてから、データベース メールのホスト データベースを構成する必要があります。  
  
 **データベース メール構成ウィザード**を使用してデータベース メールを構成すると、`msdb` データベースのデータベース メール拡張ストアド プロシージャが有効になります。 **データベース メール構成ウィザード**を使用する場合、以下の例の `sp_configure` を使用する必要はありません。  
  
 **Database Mail XPs** オプションを `0` に設定すると、データベース メールは開始されません。 データベース メールが実行されている場合にこのオプションを `0` に設定すると、`DatabaseMailExeMinimumLifeTime` オプションで設定したアイドル状態の時間が続くまで、データベース メールは継続して実行され、メールが送信されます。  
  
## <a name="examples"></a>使用例
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
