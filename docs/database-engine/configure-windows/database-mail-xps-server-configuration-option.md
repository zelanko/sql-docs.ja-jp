---
title: Database Mail XPs サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2017
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
manager: craigg
ms.openlocfilehash: c490e0762bac42aec7cba46bbad15f65bfacae48
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47753950"
---
# <a name="database-mail-xps-server-configuration-option"></a>Database Mail XPs サーバー構成オプション
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  **Database Mail XPs** オプションを使用して、サーバーのデータベース メールを有効にします。 可能な値は次のとおりです。  
  
-   **0** : データベース メールが使用できないことを示します (既定値)。  
  
-   **1** : データベース メールが使用できることを示します。  
  
 この設定は、サーバーを停止して再起動しなくてもすぐに有効になります。  
  
 データベース メールを使用するには、データベース メールを有効にしてから、データベース メールのホスト データベースを構成する必要があります。  
  
 **データベース メール構成ウィザード** を使用してデータベース メールを構成すると、 **msdb** データベースのデータベース メール拡張ストアド プロシージャが有効になります。 **データベース メール構成ウィザード**を使用する場合、以下の例の **sp_configure** を使用する必要はありません。  
  
 **Database Mail XPs** オプションを 0 に設定すると、データベース メールは開始されません。 データベース メールが実行されている場合にこのオプションを 0 に設定すると、 **DatabaseMailExeMinimumLifeTime** オプションで設定したアイドル状態の時間が続くまで、データベース メールは継続して実行され、メールが送信されます。  
  
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
  
## <a name="see-also"></a>参照  
 [データベース メール](../../relational-databases/database-mail/database-mail.md)  
  
  
