---
title: 記述子ハンドルの取得 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], retrieving or setting field values
ms.assetid: 936f983f-c7e9-43f3-97ea-dd4b1bbf4654
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c17b693080c2727d2ee788b74f247d86d7a3cb27
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302347"
---
# <a name="obtaining-descriptor-handles"></a>記述子ハンドルの取得
アプリケーションは、明示的に割り当てられた記述子のハンドルを**SQLAllocHandle**呼び出しの出力引数として取得します。 暗黙的に割り当てられた記述子のハンドルは、 **SQLGetStmtAttr**を呼び出すことによって取得されます。
