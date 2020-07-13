---
title: 記述子とデスクトップデータベースドライバー |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- desktop database drivers [ODBC], descriptors
- Jet-based ODBC drivers [ODBC], descriptors
- descriptors [ODBC], Jet-supported descriptor fields
- ODBC desktop database drivers [ODBC], descriptors
ms.assetid: 9ae2d9b5-365f-4f0a-9116-defe9498b401
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4ef79855f71d23e5a884822371f1894eb83442a9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303513"
---
# <a name="descriptors-and-desktop-database-drivers"></a>記述子およびデスクトップ データベース ドライバー
記述子は、列データまたは動的パラメーターに関する情報を保持するデータ構造です。 **SQLGetDescField**は、次に示すサポートされている記述子を取得するために使用できます。 **SQLDescribeParam**はサポートされていないため、実装パラメーター記述子 (IPD) は自動的に設定されません。 Jet で使用できない記述子フィールド (SQL_DESC_BASE_TABLE_NAME など) もサポートされていません。  
  
 Jet でサポートされる記述子フィールドの詳細については、 *『 Microsoft Jet データベースエンジンプログラマーズガイド』* を参照してください。  
  
 記述子の詳細については、 *ODBC プログラマーリファレンス*の「記述子」のトピックを参照してください。  
  
|記述子フィールド|サポート レベル|  
|-----------------------|-------------------|  
|SQL_DESC_ALLOC_TYPE|サポートされています|  
|SQL_DESC_ARRAY_SIZE|サポート対象|  
|SQL_DESC_ARRAY_STATUS_PTR|サポートされています|  
|SQL_DESC_BIND_OFFSET_PTR|サポートされています|  
|SQL_DESC_BIND_TYPE|サポートされています|  
|SQL_DESC_COUNT|サポートされています|  
|SQL_DESC_ROWS_PROCESSED_PTR|サポート対象|  
|SQL_DESC_AUTO_UNIQUE_VALUE|サポートされています|  
|SQL_DESC_BASE_COLUMN_NAME|サポートされている (新規)|  
|SQL_DESC_BASE_TABLE_NAME|サポートされている (新規)|  
|SQL_DESC_CASE_SENSITIVE|常に FALSE|  
|SQL_DESC_CATALOG_NAME|サポートされていません|  
|SQL_DESC_CONCISE_TYPE|サポートされています|  
|SQL_DESC_DATA_PTR|サポートされています|  
|SQL_DESC_DATETIME_INTERVAL_CODE|サポートされています|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|INTERVAL C 型でサポートされます|  
|SQL_DESC_DISPLAY_SIZE|サポートされています|  
|SQL_DESC_FIXED_PREC_SCALE|サポート (money では TRUE)|  
|SQL_DESC_INDICATOR_PTR|サポートされています|  
|SQL_DESC_LABEL|サポートされています|  
|SQL_DESC_LENGTH|サポートされています|  
|SQL_DESC_LITERAL_PREFIX|サポートされています|  
|SQL_DESC_LITERAL_SUFFIX|サポートされています|  
|SQL_DESC_LOCAL_TYPE_NAME|サポートされていません (空の文字列を返します)|  
|SQL_DESC_NAME|サポートされています|  
|SQL_DESC_NULLABLE|サポートされています<br /><br /> **メモ**Jet 4.0 より前のバージョンではサポートされません|  
|SQL_DESC_NUM_PREC_RADIX|サポートされています|  
|SQL_DESC_OCTET_LENGTH|サポートされています|  
|SQL_DESC_OCTET_LENGTH_PTR|サポートされています|  
|SQL_DESC_PARAMETER_TYPE|入力パラメーターのみ|  
|SQL_DESC_PRECISION|サポートされています|  
|SQL_DESC_SCALE|サポートされています|  
|SQL_DESC_SCHEMA_NAME|サポートされていません|  
|SQL_DESC_SEARCHABLE|サポートされています|  
|SQL_DESC_TABLE_NAME|サポートされていません|  
|SQL_DESC_TYPE|サポートされています|  
|SQL_DESC_TYPE_NAME|サポートされています|  
|SQL_DESC_UNNAMED|サポートされています|  
|SQL_DESC_UNSIGNED|サポートされています|  
|SQL_DESC_UPDATABLE|サポートされています|
