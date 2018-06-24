---
title: MSSQLSERVER_17130 | Microsoft Docs
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
- 17130 (Database Engine error)
ms.assetid: 7ce6afca-221d-402f-89df-da7e74a339a8
caps.latest.revision: 16
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: e4f8a2414ef1d1aba309bdbaffdbcce1d6494a87
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36072771"
---
# <a name="mssqlserver17130"></a>MSSQLSERVER_17130
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|17130|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|INIT_NOLOCKSPACE|  
|メッセージ テキスト|構成されたロック数に対するメモリが不足しています。 より小さいロックのハッシュ テーブルで開始しますが、パフォーマンスに影響する場合があります。 データベース管理者に連絡して、データベース エンジンのこのインスタンスに割り当てるメモリを増やすように構成してください。|  
  
## <a name="explanation"></a>説明  
 ロック マネージャーのハッシュ テーブルの必要なサイズに対してメモリが不足しています。  より小さいハッシュ テーブルの割り当てが試行されます。  
  
## <a name="user-action"></a>ユーザーの操作  
 サーバーのメモリ構成パラメーター (min/max server memory) を確認し、メモリ負荷を確認します。 SQL Server へのメモリの割り当てを増やします。  
  
  