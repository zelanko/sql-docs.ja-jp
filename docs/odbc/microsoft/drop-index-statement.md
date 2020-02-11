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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 23823e53e516324832c79706e6171b48a9c5297c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68071858"
---
# <a name="drop-index-statement"></a>DROP INDEX ステートメント
Microsoft Access、dBASE、または Paradox ドライバーが使用されている場合、DROP INDEX ステートメントの構文は "DROP INDEX a on b" になります。ここで、"a" はインデックスの名前、"b" はテーブルの名前 (DROP INDEX*インデックス名*ではありません) です。  
  
 Paradox ドライバーを使用すると、DROP INDEX ステートメントによって、Paradox セカンダリインデックスファイルが削除されます。  
  
 DROP INDEX ステートメントは、Microsoft Excel またはテキストドライバーではサポートされていません。
