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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fe489222c026c1499135b716f0485bb04f51bad9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68069770"
---
# <a name="freeing-descriptors"></a>記述子の解放
明示的に割り当てられた記述子は、明示的に解放することができます。これを行うには、SQL_HANDLE_DESC の*Handletype*を使用して**sqlfreehandle**を呼び出すか、接続ハンドルが解放されたときに暗黙的にこの 明示的に割り当てられた記述子が解放されると、解放された記述子が適用されるすべてのステートメントハンドルが、暗黙的に割り当てられた記述子に自動的に戻されます。  
  
 暗黙的に割り当てられた記述子は、 **Sqldisconnect**を呼び出すことによってのみ解放できます。この場合、接続で開かれているステートメントまたは記述子が削除されます。または、SQL_HANDLE_STMT の*handletype*を使用して**sqlfreehandle**を呼び出して、ステートメントハンドルおよびステートメントに関連付けられている暗黙的に割り当てられたすべての記述子 SQL_HANDLE_DESC の*Handletype*で**sqlfreehandle**を呼び出すことによって、暗黙的に割り当てられた記述子を解放することはできません。  
  
 解放された場合でも、暗黙的に割り当てられた記述子は有効なままで、そのフィールドに対して**SQLGetDescField**を呼び出すことができます。
