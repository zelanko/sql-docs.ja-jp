---
title: ExtendedAnsiSQL を設定して新しいデータ型の有効化 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- extendedANSISQL [ODBC], enabling new data types
ms.assetid: f2865543-7fff-44fa-9a6a-968bec33acdc
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4c9f7c4c66bebb2404ef8477ed85e0f36edc1407
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32902497"
---
# <a name="enabling-new-data-types-by-setting-extendedansisql"></a>ExtendedAnsiSQL を設定して新しいデータ型の有効化
ExtendedAnsiSQL フラグがオンにすると、2 つの新しいデータ型は Jet 4.0 データベースで使用できる: SQL_DECIMAL と SQL_NUMERIC です。 既定の有効桁数と小数点以下桁数は 18 と 0、それぞれします。 SQL_DECIMAL または SQL_NUMERIC として型指定された ODBC 経由でアクセスされるデータは、Microsoft Jet 10 進数の通貨の代わりにマップされます。  
  
 ExtendedAnsiSQL フラグがオフの場合、型の decimal 型または numeric でテーブルを作成することはできず、SQLGetTypeInfo() にこれらの型は表示されません。 ただし、テーブルに新しいデータ型が含まれている場合は、正しいデータ型と、使用できます。
