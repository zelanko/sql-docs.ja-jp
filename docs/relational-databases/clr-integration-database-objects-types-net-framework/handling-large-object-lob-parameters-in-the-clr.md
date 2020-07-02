---
title: CLR でのラージオブジェクト (LOB) パラメーターの処理 |Microsoft Docs
description: この記事では SQL Server CLR 統合でパラメーターのラージオブジェクト (LOB) 値を処理する方法について説明します。 LOB 型には SqlBytes と Sqlbytes を使用します。
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
ms.openlocfilehash: 0b10ac8c1ac9ccba804b892617df0b8d6c0d2f14
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85637488"
---
# <a name="handling-large-object-lob-parameters-in-the-clr"></a>CLR での LOB (ラージ オブジェクト) パラメーターの処理
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  **Sqlbytes**と**sqlbytes**を使用して、ラージオブジェクト (lob) バイナリ型 (**varbinary (MAX)**) パラメーターと lob 文字型 (**nvarchar (max)**) パラメーターをそれぞれ渡します。 これらの型を使用すると、マネージド領域に LOB 値全体をコピーするのではなく、データベースから CLR (共通言語ランタイム) ルーチンに LOB 値をストリーミングできます。 **Sqlbinary**と**SqlString**は、小さなバイナリ値と文字列値に対してのみ使用してください。  
  
## <a name="see-also"></a>関連項目  
 [.NET Framework での SQL Server データ型](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
