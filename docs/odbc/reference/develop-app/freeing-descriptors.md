---
title: 解放 (記述子を) |Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305603"
---
# <a name="freeing-descriptors"></a>記述子の解放
明示的に割り当てられた記述子は、明示的に解放することができます。これを行うには、SQL_HANDLE_DESC の*Handletype*を使用して**sqlfreehandle**を呼び出すか、接続ハンドルが解放されたときに暗黙的にこの 明示的に割り当てられた記述子が解放されると、解放された記述子が適用されるすべてのステートメントハンドルが、暗黙的に割り当てられた記述子に自動的に戻されます。  
  
 暗黙的に割り当てられた記述子は、 **Sqldisconnect**を呼び出すことによってのみ解放できます。この場合、接続で開かれているステートメントまたは記述子が削除されます。または、SQL_HANDLE_STMT の*handletype*を使用して**sqlfreehandle**を呼び出して、ステートメントハンドルおよびステートメントに関連付けられている暗黙的に割り当てられたすべての記述子 SQL_HANDLE_DESC の*Handletype*で**sqlfreehandle**を呼び出すことによって、暗黙的に割り当てられた記述子を解放することはできません。  
  
 解放された場合でも、暗黙的に割り当てられた記述子は有効なままで、そのフィールドに対して**SQLGetDescField**を呼び出すことができます。
