---
title: MSSQLSERVER_9003 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9003 (Database Engine error)
ms.assetid: 7fdfb391-5c6f-428b-b434-6c3d0b30fd7b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 33fc97759f43b58fdb7066ce6da957ea9311a491
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/21/2020
ms.locfileid: "86550757"
---
# <a name="mssqlserver_9003"></a>MSSQLSERVER_9003
    
## <a name="details"></a>詳細  
  
|属性|値|  
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
  
  
