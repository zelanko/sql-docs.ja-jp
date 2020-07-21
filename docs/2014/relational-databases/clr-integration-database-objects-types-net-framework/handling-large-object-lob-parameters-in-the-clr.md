---
title: CLR でのラージオブジェクト (LOB) パラメーターの処理 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- large data, CLR integration
- LOB data [SQL Server], CLR integration
- SqlBytes data type
- SqlChars data type
ms.assetid: d07956f6-9543-4476-9426-536f95991150
author: rothja
ms.author: jroth
ms.openlocfilehash: ee791c73a6610761c2086723f9e41c2351b37dd0
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84954752"
---
# <a name="handling-large-object-lob-parameters-in-the-clr"></a>CLR での LOB (ラージ オブジェクト) パラメーターの処理
  `SqlBytes` と `SqlChars` は、それぞれ、LOB (ラージ オブジェクト) バイナリ型 (`varbinary(max)`) パラメーターと LOB 文字型 (`nvarchar(max)`) パラメーターを渡すために使用します。 これらの型を使用すると、マネージド領域に LOB 値全体をコピーするのではなく、データベースから CLR (共通言語ランタイム) ルーチンに LOB 値をストリーミングできます。 `SqlBinary` と `SqlString` は、小さなバイナリ値や文字列値のみに使用する必要があります。  
  
## <a name="see-also"></a>参照  
 [.NET Framework での SQL Server データ型](sql-server-data-types-in-the-net-framework.md)  
  
  
