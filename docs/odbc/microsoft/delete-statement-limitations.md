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
ms.openlocfilehash: eb2587f733f5042436144f7865627fee576e3d9c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68096309"
---
# <a name="delete-statement-limitations"></a>DELETE ステートメントの制限事項
DELETE ステートメントは、Microsoft Excel またはテキストドライバーではサポートされていません。 Text ドライバーでは INSERT ステートメントがサポートされていることに注意してください。  
  
 DBASE ドライバーでは、"deleted" 値を削除するためのテーブルのパッキングはサポートされていません。  
  
 Paradox ドライバーでテーブルから行を削除するには、テーブルに一意のインデックス (Paradox 主キー) が含まれている必要があります。
