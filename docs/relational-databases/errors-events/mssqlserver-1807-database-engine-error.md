---
title: MSSQLSERVER_1807 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 1807 (Database Engine error)
ms.assetid: 13c1b240-098b-4d9e-89aa-21599548e074
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7b099b983579c9a22f4105711f886c5512c1d139
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47618320"
---
# <a name="mssqlserver1807"></a>MSSQLSERVER_1807
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|1807|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|CANNOT_EX_LOCK|  
|メッセージ テキスト|データベース '%.*ls' を排他的にロックできませんでした。 後でこの操作を再試行してください。|  
  
## <a name="explanation"></a>説明  
データベースに対して排他的なアクセスを必要とする操作で、排他ロックを獲得できませんでした。  
  
## <a name="user-action"></a>ユーザーの操作  
このデータベースに対する接続をすべて切断するか、クエリを後で再試行します。  
  
