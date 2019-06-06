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
manager: jroth
ms.openlocfilehash: a3a206a21cf7c6680a656c89c48b8f52d1069d78
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66702117"
---
# <a name="cursor-and-lock-characteristics"></a>カーソルとロックの特性
カーソルの特性は、プロバイダーの機能に依存して、次の長所と短所一般的に適用されますカーソルとロックのさまざまな種類。  
  
|カーソルまたはロックの種類|長所|欠点|  
|-------------------------|----------------|-------------------|  
|**adOpenForwardOnly**|-低のリソース要件|-逆方向にスクロールことはできません。<br />-データの同時実行|  
|**adOpenStatic**|スクロール|-データの同時実行|  
|**adOpenKeyset**|いくつかのデータの同時実行<br />スクロール|上位のリソース要件<br />-切断されたシナリオでは使用できません|  
|**adOpenDynamic**|-高のデータの同時実行<br />スクロール|-最高のリソース要件<br />-切断されたシナリオでは使用できません|  
|**adLockReadOnly**|-低のリソース要件<br />可用性が高くスケーラブルです|-カーソルによって更新不可のデータ|  
|**adLockBatchOptimistic**|バッチの更新プログラム<br />-切断されたシナリオを許可します。<br />-その他のユーザー データにアクセスできます。|データを一度に複数のユーザーによって変更できます。|  
|**adLockPessimistic**|ロック中に他のユーザーがデータを変更ことはできません。|ロック中にデータへのアクセスを他のユーザーを防止します。|  
|**adLockOptimistic**|-その他のユーザー データにアクセスできます。|データを一度に複数のユーザーによって変更できます。|
