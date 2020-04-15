---
title: 記述子を解放する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLFreeHandle function [ODBC]
- descriptors [ODBC], allocating and freeing
- freeing descriptors [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 317213f4-0ebb-4bf8-a37a-4d6b1313823f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: af30ceb29e032764b89aa2069086aa898a7d35db
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305603"
---
# <a name="freeing-descriptors"></a>記述子の解放
明示的に割り当てられた記述子は、SQL_HANDLE_DESCの*HandleType*を指定して**SQLFreeHandle**を呼び出すことによって明示的に解放するか、接続ハンドルが解放されたときに暗黙的に解放できます。 明示的に割り当てられた記述子が解放されると、解放された記述子が適用されたすべてのステートメント ハンドルが、暗黙的に割り当てられた記述子に自動的に戻ります。  
  
 暗黙的に割り当てられた記述子を解放するには**SQLFreeHandle**SQL_HANDLE_STMT、SQLDisconnect を呼び出すことによってのみ解放できます。 **SQLDisconnect** *HandleType* 暗黙的に割り当てられた記述子は、ハンドル*型*のSQL_HANDLE_DESCを使用して**SQLFreeHandle**を呼び出して解放することはできません。  
  
 解放された記述子は、解放されても有効なままであり **、SQLGetDescField**はそのフィールドで呼び出すことができます。
