---
title: MSSQLSERVER_360 | Microsoft Docs
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
- 360 (Database Engine error)
ms.assetid: e2b7c1b2-3679-4206-9b25-6bd55ef96a2c
caps.latest.revision: 11
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 2300cb7f2e45ca9ab76b9c8b7da23e5cb59e364c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36073259"
---
# <a name="mssqlserver360"></a>MSSQLSERVER_360
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|360|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DML_UPDATE_SPARSE_AND_COLSET|  
|メッセージ テキスト|INSERT、UPDATE、または MERGE ステートメントの対象の列リストには、スパース列と、スパース列を含む列セットの両方を含めることはできません。 スパース列と列セットの両方ではなく、いずれかを含めるようにステートメントを書き直してください。|  
  
## <a name="explanation"></a>説明  
 列セットは、型指定されていない XML 表現であり、テーブルの複数の列を 1 つにまとめて構造化した出力です。 列セットと、列セットに含まれる列の両方を変更しようとして、同じ列への参照が 2 つ発生しました。  
  
## <a name="user-action"></a>ユーザーの操作  
 列または列セットのいずれかへの参照を含めるようにステートメントを書き直して、両方をステートメントに含めないでください。  
  
  