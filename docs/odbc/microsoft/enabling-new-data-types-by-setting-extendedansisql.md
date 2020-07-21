---
title: ExtendedAnsiSQL | を設定して新しいデータ型を有効にするMicrosoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b703c5c14c4743e13feee139d16e5dfeb3c24c63
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303413"
---
# <a name="enabling-new-data-types-by-setting-extendedansisql"></a>ExtendedAnsiSQL を設定して新しいデータ型の有効化
ExtendedAnsiSQL フラグが有効になっている場合、Jet 4.0 データベースでは、SQL_DECIMAL と SQL_NUMERIC の2つの新しいデータ型を使用できます。 既定の有効桁数と小数点以下桁数はそれぞれ18と0です。 SQL_DECIMAL または SQL_NUMERIC として入力された ODBC を介してアクセスされるデータは、通貨ではなく Microsoft Jet Decimal にマップされます。  
  
 ExtendedAnsiSQL フラグがオフになっている場合、decimal 型または numeric 型のテーブルを作成することはできません。これらの型は SQLGetTypeInfo () には表示されません。 ただし、テーブルに新しいデータ型が含まれている場合は、正しいデータ型で使用できます。
