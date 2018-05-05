---
title: SQLBulkOperations で行を挿入する |Microsoft ドキュメント
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
- SQLBulkOperations function [ODBC], inserting rows
- data updates [ODBC], SQLBulkOperations
- updating data [ODBC], SQLBulkOperations
ms.assetid: ed585ea7-4d56-4df9-8dc3-53ca82382450
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fbeb779917c2029576bc78ec4a1d144716b7242f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="inserting-rows-with-sqlbulkoperations"></a>SQLBulkOperations で行を挿入します。
データを挿入する**SQLBulkOperations**でデータを更新するような**SQLBulkOperations**バインドされたアプリケーション バッファーからデータを使用しているためです。  
  
 新しい行の各列に値を持つように SQL_COLUMN_IGNORE の長さまたはインジケーターの値を持つ列がバインドされているすべてと、すべての非バインド列の NULL 値を受け入れるか既定値を持つ必要があります。  
  
 持つ行を挿入する**SQLBulkOperations**アプリケーションは、次を実行します。  
  
1.  SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性を挿入する行の数に設定し、バインドされたアプリケーションのバッファーに新しいデータ値を格納します。 長い形式のデータを送信する方法について**SQLBulkOperations**を参照してください[長い形式のデータおよび SQLSetPos SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md)です。  
  
2.  必要に応じて、各列の長さ/インジケーター バッファーの値を設定します。 これは、バイナリのバッファー、および SQL_NULL_DATA を NULL に設定する列にバインドされた列のデータのバイト長文字列バッファーにバインドされている列のデータまたは SQL_NTS のバイト長です。 アプリケーションは、(存在する場合、既定値に設定するのには、これらの列または SQL_COLUMN_IGNORE を NULL (1 つでない場合) の長さ/インジケーター バッファーの値を設定します。  
  
3.  呼び出し**SQLBulkOperations**で、*操作*引数 SQL_ADD に設定します。  
  
 後に**SQLBulkOperations**が返される、現在の行は変更されません。 ブックマーク列 (列 0) がバインドされている場合**SQLBulkOperations**その列にバインドされている行セットのバッファーに挿入された行のブックマークを返します。
