---
title: カーソルとロックの特性 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- locks [ADO], characteristics
- adOpenDynamic [ADO]
- cursors [ADO], characteristics
ms.assetid: 459c29cb-4230-42bf-8cc2-f3132ccc7aba
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a8507be55ae84a3a03fd75871106bc39e0631d89
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47678430"
---
# <a name="cursor-and-lock-characteristics"></a>カーソルとロックの特性
カーソルの特性は、プロバイダーの機能に依存して、次の長所と短所一般的に適用されますカーソルとロックのさまざまな種類。  
  
|カーソルまたはロックの種類|利点があります。|欠点|  
|-------------------------|----------------|-------------------|  
|**adOpenForwardOnly**|-低のリソース要件|-逆方向にスクロールことはできません。<br />-データの同時実行|  
|**adOpenStatic**|スクロール|-データの同時実行|  
|**adOpenKeyset**|いくつかのデータの同時実行<br />スクロール|上位のリソース要件<br />-切断されたシナリオでは使用できません|  
|**adOpenDynamic**|-高のデータの同時実行<br />スクロール|-最高のリソース要件<br />-切断されたシナリオでは使用できません|  
|**adLockReadOnly**|-低のリソース要件<br />可用性が高くスケーラブルです|-カーソルによって更新不可のデータ|  
|**adLockBatchOptimistic**|バッチの更新プログラム<br />-切断されたシナリオを許可します。<br />-その他のユーザー データにアクセスできます。|データを一度に複数のユーザーによって変更できます。|  
|**adLockPessimistic**|ロック中に他のユーザーがデータを変更ことはできません。|ロック中にデータへのアクセスを他のユーザーを防止します。|  
|**adLockOptimistic**|-その他のユーザー データにアクセスできます。|データを一度に複数のユーザーによって変更できます。|
