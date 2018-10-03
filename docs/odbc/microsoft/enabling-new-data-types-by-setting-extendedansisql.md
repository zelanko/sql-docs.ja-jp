---
title: ExtendedAnsiSQL を設定して新しいデータ型の有効化 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- extendedANSISQL [ODBC], enabling new data types
ms.assetid: f2865543-7fff-44fa-9a6a-968bec33acdc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 80a86ef188796883e76c6d5f6149a3e40afd341b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47692162"
---
# <a name="enabling-new-data-types-by-setting-extendedansisql"></a>ExtendedAnsiSQL を設定して新しいデータ型の有効化
ExtendedAnsiSQL フラグがオンにすると、2 つの新しいデータ型は Jet 4.0 データベースで使用できる: SQL_DECIMAL と SQL_NUMERIC します。 既定の有効桁数と小数点 18 と 0 をそれぞれされます。 SQL_DECIMAL または SQL_NUMERIC として型指定された ODBC 経由でアクセスされるデータは、Microsoft Jet を decimal 型に通貨の代わりにマップされます。  
  
 ExtendedAnsiSQL フラグがオフの場合は、10 進数または数値の型を持つテーブルを作成することはできず、SQLGetTypeInfo() にこれらの型が表示されません。 ただし、テーブルに新しいデータ型が含まれている場合は、適切なデータ型が使用できます。
