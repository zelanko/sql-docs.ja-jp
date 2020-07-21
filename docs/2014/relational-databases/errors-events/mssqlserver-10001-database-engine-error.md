---
title: MSSQLSERVER_10001 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10001 (Database Engine error)
ms.assetid: f8fd2d8d-a4af-4b6a-ba51-9123b7e4c9bf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9fe3b41642150d7fe6587e6747d2a2c72ab26700
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/21/2020
ms.locfileid: "86554207"
---
# <a name="mssqlserver_10001"></a>MSSQLSERVER_10001
    
## <a name="details"></a>詳細  
  
|属性|値|  
|-|-|  
|製品名|SQL Server|  
|イベント ID|10001|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|HR_E_UNEXPECTED|  
|メッセージ テキスト|プロバイダーが予期しない重大なエラーをレポートしました。|  
  
## <a name="explanation"></a>説明  
 分散クエリ処理で、OLE DB プロバイダーを呼び出すときに一般的なエラーが発生しました。  
  
## <a name="user-action"></a>ユーザーの操作  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用して OLE DB トレース イベントを収集し、このデータを OLE DB プロバイダーの製品サポートに提供します。  
  
## <a name="see-also"></a>参照  
 [SQL Server プロファイラーのテンプレートと権限](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
