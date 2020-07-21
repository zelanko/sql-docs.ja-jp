---
title: 予約された日付と時刻のデータ型の後に指定された UDT&#39;s を削除します |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- time data type [SQL Server], UDTs
- date data type [SQL Server], UDTs
ms.assetid: 48f109af-b1d1-4f03-a7e3-8a0b05ed94e8
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 827f060b309a7a620fd448554b074f45d78d3cb0
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059140"
---
# <a name="remove-udt39s-named-after-the-reserved-date-and-time-data-types"></a>予約された日付と時刻のデータ型の後に指定された UDT&#39;s を削除します
  アップグレード アドバイザーによって、`date` データ型または `time` データ型に予約されている語句に基づいて名前が付けられたユーザー定義型 (UDT) が検出されました。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>説明  
 データ型に使用される語句を共通言語ランタイム (CLR) またはエイリアス UDT の名前として使用しないでください。  
  
## <a name="corrective-action"></a>修正措置  
 データ型に基づいて名前が付けられた UDT を削除し、予約されていない名前を使用して UDT を再作成します。  
  
  
