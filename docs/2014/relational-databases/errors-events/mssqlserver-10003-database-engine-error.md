---
title: MSSQLSERVER_10003 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10003 (Database Engine error)
ms.assetid: 9e2cb199-f077-4d88-8117-1b7550afc696
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 719f541b31c9b537a6fee75970567f24eb50f674
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/21/2020
ms.locfileid: "86554227"
---
# <a name="mssqlserver_10003"></a>MSSQLSERVER_10003
    
## <a name="details"></a>詳細  
  
|属性|値|  
|-|-|  
|製品名|SQL Server|  
|イベント ID|10003|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|HR_E_OUTOFMEMORY|  
|メッセージ テキスト|プロバイダーのメモリが不足しました。|  
  
## <a name="explanation"></a>説明  
 システム メモリが少ないため、OLE DB プロバイダーのメモリが不足しました。  
  
## <a name="user-action"></a>ユーザーの操作  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスを再起動します。 問題が解決しない場合は、コンピューターを再起動します。 それでも問題が解決しない場合は、[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用して OLE DB トレース イベントを収集し、このデータを OLE DB プロバイダーの製品サポートに提供します。  
  
## <a name="see-also"></a>参照  
 [SQL Server プロファイラーのテンプレートと権限](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
