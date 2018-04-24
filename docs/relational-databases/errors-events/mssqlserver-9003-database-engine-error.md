---
title: MSSQLSERVER_9003 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 9003 (Database Engine error)
ms.assetid: 7fdfb391-5c6f-428b-b434-6c3d0b30fd7b
caps.latest.revision: 15
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5b7adb565f1d52afa9586b5bc47b02908264961c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver9003"></a>MSSQLSERVER_9003
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|9003|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|LOG_INVALID_LSN|  
|メッセージ テキスト|データベース '%.*ls' のログ スキャンに渡されたログ スキャン番号 %S_LSN は無効です。 このエラーはデータの破損か、またはログ ファイル (.ldf) がデータ ファイル (.mdf) に一致しないことを示している可能性があります。 このエラーがレプリケーション中に発生した場合は、パブリケーションを再作成してください。 この問題が原因でスタートアップ中にエラーが発生した場合は、バックアップから復元してください。|  
  
## <a name="explanation"></a>説明  
コンポーネントによって、無効なログ シーケンス番号がデータベースのログ マネージャーに渡されました。 レプリケーション、破損、またはプライマリ データ ファイルとログの間の不整合が考えられます。  
  
## <a name="user-action"></a>ユーザーの操作  
これがレプリケーション中に発生した場合は、パブリケーションを再作成してください。 それ以外の場合は、バックアップから復元してください。  
  
