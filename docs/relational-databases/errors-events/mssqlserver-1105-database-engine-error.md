---
title: MSSQLSERVER_1105 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 1105 (Database Engine error)
ms.assetid: e7f4ad02-8c7f-4bb9-9781-2c86253f2138
caps.latest.revision: "19"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 4a76361f4aa307eeece1e57b8e2b0c9b51c07df0
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver1105"></a>MSSQLSERVER_1105
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|1105|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|NO_MORE_SPACE_IN_FG|  
|メッセージ テキスト|データベース '%.\*ls' にオブジェクト '%.*ls'%.\*ls の領域を割り当てられませんでした。'%.\*ls' ファイル グループがいっぱいです。 不要なファイルの削除、ファイル グループ内のオブジェクトの削除、ファイル グループへの新しいファイルの追加、またはファイル グループの既存のファイルの自動拡張の設定のいずれかを行ってディスク領域を作成してください。|  
  
## <a name="explanation"></a>説明  
ファイル グループでディスク領域が不足しています。  
  
## <a name="user-action"></a>ユーザーの操作  
次の操作により、ファイル グループで領域を使用できるようになることがあります。  
  
-   AUTOGROW をオンにする。  
  
-   ファイル グループにファイルをさらに追加する。  
  
-   不要になったインデックスやテーブルを削除することにより、ディスク領域を解放する。  
  
-   詳細については、SQL Server オンライン ブックの「データ ディスク領域の不足に関するトラブルシューティング」を参照してください。  
  
> [!NOTE]  
> 1 つのインデックスが複数のファイルに存在している場合に、いずれかのファイルがいっぱいになると、**ALTER INDEX REORGANIZE** からエラー 1105 が返される可能性があります。 いっぱいになったファイルに行を移動しようとしたときに、再構成プロセスはブロックされます。 この制限を回避するには、**ALTER INDEX REORGANIZE** ではなく **ALTER INDEX REBUILD** を実行するか、いっぱいになったファイルの拡張制限を大きくしてください。  
  
