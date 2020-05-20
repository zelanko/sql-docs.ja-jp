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
author: rothja
ms.author: jroth
ms.openlocfilehash: 02f4be413ddcfc9215cdbf12142b883ade644f41
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82761118"
---
# <a name="cursor-and-lock-characteristics"></a>カーソルとロックの特性
カーソルの特性はプロバイダーの機能によって異なりますが、一般的に、次のような長所と短所がさまざまな種類のカーソルやロックに適用されます。  
  
|カーソルまたはロックの種類|長所|短所|  
|-------------------------|----------------|-------------------|  
|**adOpenForwardOnly**|-リソース要件が不足しています|-後方にスクロールできません<br />-データの同時実行がありません|  
|**adOpenStatic**|-スクロール可能|-データの同時実行がありません|  
|**adOpenKeyset**|-データの同時実行<br />-スクロール可能|-より高いリソース要件<br />-切断されたシナリオでは使用できません|  
|**adOpenDynamic**|-高データ同時実行<br />-スクロール可能|-最大リソース要件<br />-切断されたシナリオでは使用できません|  
|**adLockReadOnly**|-リソース要件が不足しています<br />-拡張性が高い|-カーソルを使用して更新できないデータ|  
|**adLockBatchOptimistic**|-バッチ更新<br />-切断されたシナリオを許可します<br />-他のユーザーがデータにアクセスできる|-複数のユーザーが同時にデータを変更できます。|  
|**adLockPessimistic**|-ロック中に他のユーザーがデータを変更することはできません|-ロック中に他のユーザーがデータにアクセスできないようにします|  
|**adLockOptimistic**|-他のユーザーがデータにアクセスできる|-複数のユーザーが同時にデータを変更できます。|
