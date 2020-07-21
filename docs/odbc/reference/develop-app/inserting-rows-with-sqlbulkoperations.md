---
title: SQLBulkOperations を使用した行の挿入 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLBulkOperations function [ODBC], inserting rows
- data updates [ODBC], SQLBulkOperations
- updating data [ODBC], SQLBulkOperations
ms.assetid: ed585ea7-4d56-4df9-8dc3-53ca82382450
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a6fa384292f02026b8390aa92525144dce6f549b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300112"
---
# <a name="inserting-rows-with-sqlbulkoperations"></a>SQLBulkOperations による行の挿入
**Sqlbulkoperations**を使用したデータの挿入は、バインドされたアプリケーションバッファーのデータを使用するため、 **sqlbulkoperations**でデータを更新することと似ています。  
  
 新しい行の各列に値が含まれるように、長さ/インジケーターの値が SQL_COLUMN_IGNORE でバインドされているすべての列が NULL 値を受け入れるか、既定値を持つ必要があります。  
  
 **Sqlbulkoperations**を使用して行を挿入するために、アプリケーションは次の処理を実行します。  
  
1.  SQL_ATTR_ROW_ARRAY_SIZE ステートメントの属性を、挿入する行の数に設定し、バインドされたアプリケーションバッファーに新しいデータ値を格納します。 **Sqlbulkoperations**で長いデータを送信する方法の詳細については、「 [Long data And SQLSetPos And sqlbulkoperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md)」を参照してください。  
  
2.  各列の長さ/インジケーターバッファーの値を必要に応じて設定します。 これは、文字列バッファーにバインドされている列のデータまたは SQL_NTS のバイト長、バイナリバッファーにバインドされた列のデータのバイト長、および NULL に設定する列の SQL_NULL_DATA です。 アプリケーションは、既定値に設定される列 (存在する場合) または NULL (存在しない場合) に設定される列の長さ/インジケーターバッファーの値を SQL_COLUMN_IGNORE に設定します。  
  
3.  *操作*引数が SQL_ADD に設定された**sqlbulkoperations**を呼び出します。  
  
 **Sqlbulkoperations**が戻ると、現在の行は変更されません。 ブックマーク列 (列 0) がバインドされている場合、 **Sqlbulkoperations**は、その列にバインドされている行セットバッファー内の挿入された行のブックマークを返します。
