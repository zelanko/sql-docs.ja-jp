---
title: "SQLGetData (デスクトップ データベース ドライバー) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SQLGetData function [ODBC], Desktop Database Drivers
ms.assetid: c9d9a32d-5dc2-4189-9bfb-2b008bc3d6a3
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cdf875d594d84143ec45afca22805e533837c676
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="sqlgetdata-desktop-database-drivers"></a>SQLGetData (デスクトップ データベース ドライバー)
この関数は、その後、列が取得された順序に関係なくバインドされた列があるかどうか、任意の列からデータを取得できます。  
  
> [!NOTE]  
>  \*pcbValue **SQLGetData**返す可能性があります 2 倍の数文字を実際に使用できる Jet 4.0 データベースで 510 文字より長く ANSI データをバインドする場合。 以下の 510 文字値では、実際の cbValue を返します。
