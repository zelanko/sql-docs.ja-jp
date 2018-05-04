---
title: Sql-92 準拠 |Microsoft ドキュメント
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
- Jet-based ODBC drivers [ODBC], SQL-92 compliance
- desktop database drivers [ODBC], SQL-92 compliance
- SQL-92 compliance [ODBC]
- ODBC desktop database drivers [ODBC], SQL-92 compliance
ms.assetid: 50c8c7df-df01-4f4d-ad62-d059cf29d73a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1d6f256f16960332de497e6a861137ca42a0480f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sql-92-compliance"></a>Sql-92 準拠
デスクトップの ODBC データベース ドライバーと、基になる Microsoft Jet エンジンは、sql-92 準拠ではありません。 Sql-92 で定義されている多くの機能をサポートしています。 ドライバーでサポートされている一部の機能は、sql-92 ではサポートされていません。 詳細については、次を参照してください。、 *Microsoft Jet データベース エンジン プログラマ ガイド*です。 2 つの主な違いを次に示します。  
  
-   デスクトップ データベース ドライバーによって使用される SQL より強力な SQL 92 によって指定された式をサポートします。  
  
-   別のルールは、BETWEEN の述語に適用されます。  
  
-   デスクトップ データベース ドライバーと ANSI SQL で使用される SQL には、別のキーワードがサポートされています。  
  
 次の SQL 92 機能は、Microsoft Jet SQL ではサポートされません。  
  
-   GRANT およびロックなどのセキュリティ ステートメント  
  
-   DISTINCT 集計関数の参照を含むです。  
  
 次の機能は、sql-92 で指定されていないデスクトップ データベース ドライバーによって使用される SQL での機能強化です。  
  
-   クロス集計クエリのサポートを提供する変換ステートメント。  
  
-   その他の集計関数 (**StDev**と**VarP**)。  
  
> [!NOTE]  
>  デスクトップ データベース ドライバー構文をサポートして、標準的な ANSI % (パーセント) と _ (アンダー スコア)、されません * (アスタリスク付き) としますか? (疑問符)。
