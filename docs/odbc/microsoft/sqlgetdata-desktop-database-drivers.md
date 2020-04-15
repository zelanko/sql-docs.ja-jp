---
title: SQLGetData (デスクトップ データベース ドライバ) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetData function [ODBC], Desktop Database Drivers
ms.assetid: c9d9a32d-5dc2-4189-9bfb-2b008bc3d6a3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2b102d8435831d45aad3c2049581513e0493de9a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304123"
---
# <a name="sqlgetdata-desktop-database-drivers"></a>SQLGetData (デスクトップ データベース ドライバー)
この関数は、列の後にバインドされた列があるかどうか、および列が取得される順序に関係なく、任意の列からデータを取得できます。  
  
> [!NOTE]  
>  \***SQLGetData**の pcbValue は、Jet 4.0 データベースで 510 文字を超える ANSI データにバインドする場合に実際に使用可能な 2 倍の文字数を返す場合があります。 文字値が 510 以下の場合は、実際の cbValue が返されます。
