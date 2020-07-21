---
title: MSSQLSERVER_10003 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10003 (Database Engine error)
ms.assetid: 9e2cb199-f077-4d88-8117-1b7550afc696
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e75a5e5da30ccfc7ed035693992f8a79e3b84f1b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85781560"
---
# <a name="mssqlserver_10003"></a>MSSQLSERVER_10003
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>詳細  
  
| 属性 | 値 |  
| :-------- | :---- |  
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
[SQL Server プロファイラーのテンプレートとアクセス許可](~/tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)  
[SQL Server Native Client &#40;OLE DB&#41;](~/relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
