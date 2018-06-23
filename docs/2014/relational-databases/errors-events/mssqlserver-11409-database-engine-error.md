---
title: MSSQLSERVER_11409 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 11409 (Database Engine error)
ms.assetid: 99b71a1c-a72d-4ca9-9d00-4230c9042ba5
caps.latest.revision: 9
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 5c75da8c58a1540759eb502b49e5bf6d57abc210
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36073264"
---
# <a name="mssqlserver11409"></a>MSSQLSERVER_11409
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|11409|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|ALTERCOL_COLSET_DROP|  
|メッセージ テキスト|テーブル '%.\*ls' の列セット '%.*ls' を削除できません。テーブルに 1025 以上の列が含まれています。|  
  
## <a name="explanation"></a>説明  
 テーブルには、スパース列または計算列として指定していない列を 1024 個まで含めることができます。 スパース列が原因でテーブルの列数が 1024 を超える場合は、テーブルに列セットを定義する必要があります。 参照先のテーブルには 1025 以上の列が含まれており、このテーブルから列セットを削除しようとしました。  
  
## <a name="user-action"></a>ユーザーの操作  
 テーブルの現在の列では、列セットを保持する必要があります。  
  
 列セットを削除するには、まずテーブルから列を削除し、列数が 1024 以下になるようにします。 その後、列セットを削除できます。  
  
  