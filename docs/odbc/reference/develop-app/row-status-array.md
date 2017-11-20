---
title: "行の状態配列 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- row status array [ODBC]
- cursors [ODBC], block
- result sets [ODBC], row status array
- block cursors [ODBC]
- result sets [ODBC], block cursors
- rowset status [ODBC]
ms.assetid: 4b69f189-2722-4314-8a02-f4ffecd6dabd
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 34fe599aee975dc0c01fc1fbc36f1bed6cab6b6b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="row-status-array"></a>行の状態配列
データに加え**SQLFetch**と**SQLFetchScroll**行セット内の行ごとの状態を配列を返すことができます。 この配列は、SQL_ATTR_ROW_STATUS_PTR ステートメント属性によって指定されます。 この配列は、アプリケーションによって割り当てられているし、SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性で指定された数の要素があります。 、配列内の値が設定**SQLBulkOperations**、 **SQLFetch**、 **SQLFetchScroll**、および**SQLSetPos です。** 値では、行と最後にフェッチした後にその状態が変更するかどうかの状態について説明します。  
  
|行の状態配列の値|Description|  
|----------------------------|-----------------|  
|SQL_ROW_SUCCESS|この行は、フェッチに成功しましたれ、最後にフェッチした後は変更されていません。|  
|SQL_ROW_SUCCESS_WITH_INFO|この行は、フェッチに成功しましたれ、最後にフェッチした後は変更されていません。 ただし、行に関する警告が返されました。|  
|SQL_ROW_ERROR|行をフェッチ中にエラーが発生しました。|  
|SQL_ROW_UPDATED|この行はフェッチに成功しましたれ、最後にフェッチした後が更新されました。 行が再度フェッチまたは更新**SQLSetPos**、新規の状態にその状態が変更されました。<br /><br /> ドライバーによっては、データへの変更を検出することはできず、そのため、この値を返すことはできません。 ドライバーが行の再フェッチの更新を検出できるかどうかを決定するには、アプリケーションが呼び出す**SQLGetInfo** SQL_ROW_UPDATES オプションを使用します。|  
|SQL_ROW_DELETED|前回のフェッチ後、行が削除されました。|  
|SQL_ROW_ADDED|によって、行が挿入された**SQLBulkOperations**です。 行が再度フェッチまたはによって更新されるかどうか**SQLSetPos**、その状態は SQL_ROW_SUCCESS します。<br /><br /> この値が設定されていない**SQLFetch**または**SQLFetchScroll**です。|  
|SQL_ROW_NOROW|行セットには、結果セットの末尾がオーバー ラップされ、行の状態配列のこの要素に対応する行が返されません。|

