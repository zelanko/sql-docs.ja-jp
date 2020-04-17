---
title: CLR でのラージ オブジェクト (LOB) パラメータの処理 |マイクロソフトドキュメント
description: この資料では、SQL Server CLR 統合でパラメーターの大きなオブジェクト (LOB) 値を処理する方法について説明します。 LOB 型には Sql バイトおよび SqlChar を使用します。
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
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
ms.openlocfilehash: 0941ca2f5fc1a05397dd3dbec5e0dd27c6e5d815
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488457"
---
# <a name="handling-large-object-lob-parameters-in-the-clr"></a>CLR での LOB (ラージ オブジェクト) パラメーターの処理
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  **SqlBytes**と**SqlChars**を使用して、ラージ オブジェクト (LOB) バイナリ型 (**varbinary(max)**) と LOB 文字型 (**nvarchar(max)**) の各パラメーターを渡します。 これらの型を使用すると、マネージド領域に LOB 値全体をコピーするのではなく、データベースから CLR (共通言語ランタイム) ルーチンに LOB 値をストリーミングできます。 **SqlBinary**および**SqlString**は、小さなバイナリ文字列値と文字列値にのみ使用する必要があります。  
  
## <a name="see-also"></a>参照  
 [.NET Framework での SQL Server データ型](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
