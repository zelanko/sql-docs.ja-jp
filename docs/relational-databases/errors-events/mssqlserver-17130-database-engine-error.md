---
title: MSSQLSERVER_17130 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 17130 (Database Engine error)
ms.assetid: 7ce6afca-221d-402f-89df-da7e74a339a8
caps.latest.revision: "17"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 471f90bef5837034c332f1f423787bc02f7eaad0
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
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
  
