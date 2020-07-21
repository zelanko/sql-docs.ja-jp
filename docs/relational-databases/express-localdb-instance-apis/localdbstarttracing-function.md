---
title: LocalDBStartTracing 関数 |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
apiname:
- LocalDBStartTracing
apilocation:
- sqluserinstance.dll
apitype: DLLExport
ms.assetid: c7b83833-6d2a-4a06-9cb7-42767bed52c6
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1ece276dca136aaa5f21f9fdc1ab16ffad9ba2d7
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85765213"
---
# <a name="localdbstarttracing-function"></a>LocalDBStartTracing 関数
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  現在の Windows ユーザーが所有しているすべての SQL Server Express LocalDB インスタンスの API 呼び出しの追跡を有効にします。  
  
 **ヘッダーファイル:** sqlncli  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT LocalDBStartTracing();  
```  
  
## <a name="returns"></a>戻り値  
 S_OK  
 関数が正常に実行されました。  
  
 [LOCALDB_ERROR_XEVENT_FAILED](../../relational-databases/express-localdb-error-messages/localdb-error-xevent-failed.md)  
 LocalDB インスタンスの API 内で XEvent エンジンを開始できませんでした。  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../../relational-databases/express-localdb-error-messages/localdb-error-internal-error.md)  
 予期しないエラーが発生しました。 詳細をイベント ログで確認してください。  
  
## <a name="remarks"></a>Remarks  
 LocalDB API を使用するコードサンプルについては、 [Localdb リファレンスの SQL Server Express](../../relational-databases/sql-server-express-localdb-reference.md)を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [SQL Server Express LocalDB ヘッダーとバージョン情報](../../relational-databases/express-localdb-instance-apis/sql-server-express-localdb-header-and-version-information.md)  
  
  
