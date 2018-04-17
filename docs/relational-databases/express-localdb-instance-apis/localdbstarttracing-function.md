---
title: LocalDBStartTracing 関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: localdb
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- LocalDBStartTracing
apilocation:
- sqluserinstance.dll
apitype: DLLExport
ms.assetid: c7b83833-6d2a-4a06-9cb7-42767bed52c6
caps.latest.revision: 11
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2e2ec64d0a6e7f89eefa91a89ed2d99aac4562b8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="localdbstarttracing-function"></a>LocalDBStartTracing 関数
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  現在の Windows ユーザーが所有しているすべての SQL Server Express LocalDB インスタンスの API 呼び出しの追跡を有効にします。  
  
 **ヘッダー ファイル:** sqlncli.h  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT LocalDBStartTracing();  
```  
  
## <a name="returns"></a>返します。  
 S_OK  
 関数が正常に実行されました。  
  
 [LOCALDB_ERROR_XEVENT_FAILED](../../relational-databases/express-localdb-error-messages/localdb-error-xevent-failed.md)  
 LocalDB インスタンスの API 内で XEvent エンジンを開始できませんでした。  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../../relational-databases/express-localdb-error-messages/localdb-error-internal-error.md)  
 予期しないエラーが発生しました。 詳細をイベント ログで確認してください。  
  
## <a name="remarks"></a>解説  
 LocalDB API を使用するコード サンプルは、次を参照してください。 [SQL Server Express LocalDB リファレンス](../../relational-databases/sql-server-express-localdb-reference.md)です。  
  
## <a name="see-also"></a>参照  
 [SQL Server Express LocalDB ヘッダーとバージョン情報](../../relational-databases/express-localdb-instance-apis/sql-server-express-localdb-header-and-version-information.md)  
  
  
