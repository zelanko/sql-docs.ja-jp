---
title: SQL-92 コンプライアンス |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], SQL-92 compliance
- desktop database drivers [ODBC], SQL-92 compliance
- SQL-92 compliance [ODBC]
- ODBC desktop database drivers [ODBC], SQL-92 compliance
ms.assetid: 50c8c7df-df01-4f4d-ad62-d059cf29d73a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9ac0ae5873e545afb8fcac9dd003c984b1ed303a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300702"
---
# <a name="sql-92-compliance"></a>SQL-92 準拠
ODBC デスクトップ データベース ドライバと基になる Microsoft Jet エンジンは、SQL-92 に準拠していません。 SQL-92 で定義されている多くの機能をサポートしています。 ドライバーでサポートされている機能の一部は、SQL-92 ではサポートされていません。 詳細については、『 Microsoft *Jet データベース エンジン プログラマ ガイド 』* を参照してください。 この 2 つの主な違いは次のとおりです。  
  
-   デスクトップ データベース ドライバで使用される SQL は、SQL-92 で指定された式よりも強力な式をサポートします。  
  
-   BETWEEN 述語には、さまざまな規則が適用されます。  
  
-   デスクトップ データベース ドライバと ANSI SQL で使用される SQL では、さまざまなキーワードがサポートされています。  
  
 次の SQL-92 機能は、マイクロソフトの Jet SQL ではサポートされていません。  
  
-   GRANT や LOCK などのセキュリティ ステートメント。  
  
-   集計関数参照を持つ DISTINCT。  
  
 以下の機能は、SQL-92 で指定されていないデスクトップ データベース ドライバで使用される SQL の機能強化です。  
  
-   クロス集計クエリのサポートを提供する TRANSFORM ステートメント。  
  
-   追加の集計関数 (**StDev**および**VarP**) 。  
  
> [!NOTE]  
>  デスクトップ データベース ドライバは、標準の ANSI 構文をサポートしています( % と _ (アンダースコア) ではなく 、 * (アスタリスク) と ? (疑問符) に設定します。
