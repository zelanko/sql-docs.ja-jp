---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 086c5381f1801baf919508525c17faab93746ca0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68003360"
---
# <a name="sqlgetdata-desktop-database-drivers"></a>SQLGetData (デスクトップ データベース ドライバー)
この関数は、列の後にバインドされた列があるかどうか、および列の取得順序に関係なく、任意の列からデータを取得できます。  
  
> [!NOTE]  
>  \***SQLGetData**の pcbValue は、Jet 4.0 データベースで510文字を超える ANSI データにバインドする場合に、実際に使用できる文字数の2倍を返すことがあります。 510以下の文字値を指定すると、実際の cbValue が返されます。
