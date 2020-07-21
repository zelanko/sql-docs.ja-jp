---
title: Reserved ORDPATH data type | の後に指定された UDT&#39;s を削除します。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 474e910a-6abb-4e28-acc2-055338c011d4
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0528d19de17781d863e3a42fdef7db558fe5d190
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059133"
---
# <a name="remove-udt39s-named-after-the-reserved-ordpath-data-type"></a>Reserved ORDPATH データ型の後に指定された UDT&#39;s を削除します。
  アップグレード アドバイザーによって、`ORDPATH` データ型に予約されている語句に基づいて名前が付けられたユーザー定義型 (UDT) が検出されました。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>説明  
 組み込みデータ型に使用される語句を共通言語ランタイム (CLR) またはエイリアス UDT の名前として使用しないでください。  
  
## <a name="corrective-action"></a>修正措置  
 データ型に基づいて名前が付けられた UDT を削除し、予約されていない名前を使用して UDT を再作成します。  
  
## <a name="external-resources"></a>外部リソース  
 [ユーザー定義型を作成する](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
  
  
