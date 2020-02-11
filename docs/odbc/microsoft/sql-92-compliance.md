---
title: SQL-92 コンプライアンス |Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e5d8ed2818b466d16591be8b70478221d7ac84df
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68063367"
---
# <a name="sql-92-compliance"></a>SQL-92 準拠
ODBC デスクトップデータベースドライバーおよび基になる Microsoft Jet エンジンは、SQL 92 に準拠していません。 SQL-92 で定義されている多くの機能をサポートしています。 ドライバーでサポートされている一部の機能は、SQL-92 ではサポートされていません。 詳細については、 *『 Microsoft Jet データベースエンジンプログラマーズガイド』* を参照してください。 2つの主な違いを次に示します。  
  
-   デスクトップデータベースドライバーによって使用される SQL は、SQL-92 で指定されたものよりも強力な式をサポートします。  
  
-   BETWEEN 述語には、さまざまなルールが適用されます。  
  
-   デスクトップデータベースドライバーおよび ANSI SQL で使用される SQL では、さまざまなキーワードがサポートされています。  
  
 Microsoft Jet SQL では、次の SQL-92 機能はサポートされていません。  
  
-   GRANT や LOCK などのセキュリティステートメント。  
  
-   DISTINCT と集計関数参照。  
  
 次の機能は、SQL-92 で指定されていないデスクトップデータベースドライバーによって使用される SQL の機能強化です。  
  
-   クロス集計クエリのサポートを提供する TRANSFORM ステートメント。  
  
-   追加の集計関数 (**StDev**および**VarP**)。  
  
> [!NOTE]  
>  デスクトップデータベースドライバーでサポートされている ANSI 構文は、% (パーセント) と _ (アンダースコア) で、* (アスタリスク) および? です。 (疑問符)。
