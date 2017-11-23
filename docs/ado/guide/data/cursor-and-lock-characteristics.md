---
title: "カーソルやロック特性 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- locks [ADO], characteristics
- adOpenDynamic [ADO]
- cursors [ADO], characteristics
ms.assetid: 459c29cb-4230-42bf-8cc2-f3132ccc7aba
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 84f06591c70a42701ca264c99af00e4f072aadd0
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="cursor-and-lock-characteristics"></a>カーソルやロック特性
プロバイダーの機能によって、カーソルの特性が依存しているときに、次の長所と短所一般的に適用されますさまざまな種類のカーソルとロックします。  
  
|カーソルまたはロックの種類|利点があります。|短所|  
|-------------------------|----------------|-------------------|  
|**adOpenForwardOnly**|-低リソース要件|-後方にスクロールことはできません。<br />-データの同時実行|  
|**adOpenStatic**|スクロール|-データの同時実行|  
|**adOpenKeyset**|いくつかのデータの同時実行<br />スクロール|の下位リソース要件<br />-切断されたシナリオでは使用できません|  
|**adOpenDynamic**|-高のデータの同時実行<br />スクロール|最上位のリソース要件<br />-切断されたシナリオでは使用できません|  
|**adLockReadOnly**|-低リソース要件<br />-拡張性|データをカーソルによる更新できません。|  
|**adLockBatchOptimistic**|バッチ更新プログラム<br />-により、切断されたシナリオ<br />-その他のユーザー データにアクセスできません。|データを一度に複数のユーザーによって変更できます。|  
|**adLockPessimistic**|ロック中に他のユーザーがデータを変更ことはできません。|-ロック中にデータへのアクセスを他のユーザーを防止します。|  
|**adLockOptimistic**|-その他のユーザー データにアクセスできません。|データを一度に複数のユーザーによって変更できます。|
