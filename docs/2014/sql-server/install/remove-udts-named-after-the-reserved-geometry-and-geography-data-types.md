---
title: 予約された GEOMETRY データ型と GEOGRAPHY データ型の後に名前が付けられた Udt を削除します。Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- geometry data type [SQL Server], UDTs
- geography data type [SQL Server], UDTs
ms.assetid: a167ce3a-50b4-4e77-a884-adb23b586c72
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 4977d45d53e1114edc8e04ad504963bae0b9eb9d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059122"
---
# <a name="remove-udts-named-after-the-reserved-geometry-and-geography-data-types"></a>予約されている GEOMETRY データ型および GEOGRAPHY データ型に基づいて名前が付けられた UDT の削除
  アップグレード アドバイザーによって、`geometry` データ型または `geography` データ型に予約されている語句に基づいて名前が付けられたユーザー定義型 (UDT) が検出されました。 `geometry` データ型および `geography` データ型は、空間データ機能の一部です。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>説明  
 空間データ型に使用される語句を共通言語ランタイム (CLR) またはエイリアス UDT の名前として使用しないでください。  
  
## <a name="corrective-action"></a>修正措置  
 データ型に基づいて名前が付けられた UDT を削除し、予約されていない名前を使用して UDT を再作成します。  
  
## <a name="external-resources"></a>外部リソース  
 [ユーザー定義型を作成する](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
  
 [空間データ型の概要](../../relational-databases/spatial/spatial-data-types-overview.md)  
  
  
