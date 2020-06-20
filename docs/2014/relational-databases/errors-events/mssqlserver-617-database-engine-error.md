---
title: MSSQLSERVER_617 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 617 (Database Engine error)
ms.assetid: 213545d9-08a7-4427-bfd1-8b7e16644281
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dedf0b9ae26e7c2c1bb2c3251a1df10a3577f96d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85053780"
---
# <a name="mssqlserver_617"></a>MSSQLSERVER_617
    
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
  
  
