---
title: SQLGetData (デスクトップ データベース ドライバー) |Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 6f362d725f8b734ab9ecdbdc79c268af08a495b4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63313138"
---
# <a name="sqlgetdata-desktop-database-drivers"></a>SQLGetData (デスクトップ データベース ドライバー)
この関数は、その後に、列を取得する順序に関係なくバインドされた列があるかどうか、任意の列からデータを取得できます。  
  
> [!NOTE]  
>  \*pcbValue **SQLGetData**返す可能性があります 2 倍の数文字を実際に使用できる Jet 4.0 データベースで 510 文字より長く ANSI データにバインドする場合。 以下の 510 文字値では、実際の cbValue を返します。
