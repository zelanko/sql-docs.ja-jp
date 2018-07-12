---
title: MSSQLSERVER_617 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 617 (Database Engine error)
ms.assetid: 213545d9-08a7-4427-bfd1-8b7e16644281
caps.latest.revision: 14
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f79f2f585eeffde4cb7e81a322a7b5c089f5212a
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37431001"
---
# <a name="mssqlserver617"></a>MSSQLSERVER_617
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|617|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|NODESHASH|  
|メッセージ テキスト|データベース ID %d のオブジェクト ID %ld の記述子の非ハッシュ化を試みたときに、記述子がハッシュ テーブルに見つかりませんでした。 作業テーブルがエントリに見つかりません。 クエリを再実行してください。 カーソルが含まれている場合は、カーソルを閉じてから再度開いてください。|  
  
## <a name="explanation"></a>説明  
 SQL Server で、作業テーブルの特定のエントリが見つかりません。  
  
## <a name="user-action"></a>ユーザーの操作  
  
1.  カーソルが含まれている場合は、カーソルを閉じてから再度開いてください。  
  
2.  クエリを再実行します。  
  
  
