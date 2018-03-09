---
title: MSSQLSERVER_17130 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 17130 (Database Engine error)
ms.assetid: 7ce6afca-221d-402f-89df-da7e74a339a8
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 353945309f86c4531627315ddf41b0d012105a97
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver17130"></a>MSSQLSERVER_17130
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
  
