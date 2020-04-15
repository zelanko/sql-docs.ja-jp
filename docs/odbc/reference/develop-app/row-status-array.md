---
title: 行ステータス配列 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- row status array [ODBC]
- cursors [ODBC], block
- result sets [ODBC], row status array
- block cursors [ODBC]
- result sets [ODBC], block cursors
- rowset status [ODBC]
ms.assetid: 4b69f189-2722-4314-8a02-f4ffecd6dabd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 60dead23fe0051c05698e094f37ddad96b2b337d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304293"
---
# <a name="row-status-array"></a>行の状態の配列
データに加えて **、SQLFetch**と**SQLFetchScroll**行セット内の各行の状態を示す配列を返すことができます。 この配列は、SQL_ATTR_ROW_STATUS_PTR ステートメント属性を使用して指定されます。 この配列はアプリケーションによって割り当てられ、SQL_ATTR_ROW_ARRAY_SIZEステートメント属性で指定された数の要素が必要です。 配列内の値は **、SQL バルクオペレーション****、SQL フェッチ****、SQL フェッチスクロール**、および**SQL セットポスによって設定されます。** 値は、行の状況、および最後にフェッチされた後にその状況が変更されたかどうかを示します。  
  
|行ステータス配列値|説明|  
|----------------------------|-----------------|  
|SQL_ROW_SUCCESS|行は正常にフェッチされ、最後にフェッチされてから変更されていません。|  
|SQL_ROW_SUCCESS_WITH_INFO|行は正常にフェッチされ、最後にフェッチされてから変更されていません。 ただし、行に関する警告が返されました。|  
|SQL_ROW_ERROR|行のフェッチ中にエラーが発生しました。|  
|SQL_ROW_UPDATED|行は正常にフェッチされ、最後にフェッチされてから更新されました。 行が再びフェッチされるか **、SQLSetPos**によって更新された場合、その状態は新しい状態に変更されます。<br /><br /> 一部のドライバーは、データの変更を検出できないため、この値を返すことができません。 ドライバーが再フェッチされた行の更新を検出できるかどうかを判断するには、アプリケーションは、SQL_ROW_UPDATES オプションを使用して**SQLGetInfo**を呼び出します。|  
|SQL_ROW_DELETED|行は最後にフェッチされてから削除されています。|  
|SQL_ROW_ADDED|行は **、SQLBulkOperations**によって挿入されました。 行が再度フェッチされるか **、SQLSetPos**によって更新された場合、その状態はSQL_ROW_SUCCESS。<br /><br /> この値は **、SQL フェッチ**または**SQL フェッチスクロール**によって設定されません。|  
|SQL_ROW_NOROW|行セットは結果セットの末尾と重なり合っており、行ステータス配列のこの要素に対応する行は返されませんでした。|
