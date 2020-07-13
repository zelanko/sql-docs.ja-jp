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
ms.openlocfilehash: 6f67e4184ea54be6bcd5c2a74d3c0e0711b702f2
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85031421"
---
# <a name="mssqlserver_9003"></a>MSSQLSERVER_9003
    
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
  
  
