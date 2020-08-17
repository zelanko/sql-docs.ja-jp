---
description: SQLGetData (デスクトップ データベース ドライバー)
title: SQLGetData (デスクトップデータベースドライバー) |Microsoft Docs
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
ms.openlocfilehash: cfce744c3f4a2e0e4d9fcb054a8226538537bdcf
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340229"
---
# <a name="sqlgetdata-desktop-database-drivers"></a>SQLGetData (デスクトップ データベース ドライバー)
この関数は、列の後にバインドされた列があるかどうか、および列の取得順序に関係なく、任意の列からデータを取得できます。  
  
> [!NOTE]  
>  \***SQLGetData**の pcbValue は、Jet 4.0 データベースで510文字を超える ANSI データにバインドする場合に、実際に使用できる文字数の2倍を返すことがあります。 510以下の文字値を指定すると、実際の cbValue が返されます。
