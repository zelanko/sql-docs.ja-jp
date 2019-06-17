---
title: DELETE ステートメントの制限事項 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DELETE statement limitations [ODBC]
- ODBC SQL grammar, DELETE statement limitations
ms.assetid: 084761fe-e65b-4f38-ba4f-69884b2a7700
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 98bd56051c724186d7308eff669263d29b82ecd5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63198168"
---
# <a name="delete-statement-limitations"></a>DELETE ステートメントの制限事項
DELETE ステートメントは、Microsoft Excel またはテキストのドライバーではサポートされていません。 テキストのドライバーの INSERT ステートメントがサポートされていることに注意してください。  
  
 DBASE ドライバーでは、「削除」の値を削除するテーブルをパッキングすることはできません。  
  
 テーブルから行を削除する Paradox ドライバーの場合、テーブルに一意のインデックス (Paradox 主キー) ことが必要です。
