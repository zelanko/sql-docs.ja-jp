---
title: DROP INDEX Statement |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DROP INDEX [ODBC]
- SQL grammar [ODBC], DROP INDEX
ms.assetid: cd0ff767-9254-413b-bd1a-bed26c6774f5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 638bae6491c020519a0123ff56fe31e9a9ca1cf7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303433"
---
# <a name="drop-index-statement"></a>DROP INDEX ステートメント
Microsoft Access、dBASE、または Paradox ドライバーが使用されている場合、DROP INDEX ステートメントの構文は "DROP INDEX a on b" になります。ここで、"a" はインデックスの名前、"b" はテーブルの名前 (DROP INDEX*インデックス名*ではありません) です。  
  
 Paradox ドライバーを使用すると、DROP INDEX ステートメントによって、Paradox セカンダリインデックスファイルが削除されます。  
  
 DROP INDEX ステートメントは、Microsoft Excel またはテキストドライバーではサポートされていません。
