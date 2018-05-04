---
title: SQLGetData (デスクトップ データベース ドライバー) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLGetData function [ODBC], Desktop Database Drivers
ms.assetid: c9d9a32d-5dc2-4189-9bfb-2b008bc3d6a3
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ae546182d51663c15a14ac25b5349a06da02e952
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqlgetdata-desktop-database-drivers"></a>SQLGetData (デスクトップ データベース ドライバー)
この関数は、その後、列が取得された順序に関係なくバインドされた列があるかどうか、任意の列からデータを取得できます。  
  
> [!NOTE]  
>  \*pcbValue **SQLGetData**返す可能性があります 2 倍の数文字を実際に使用できる Jet 4.0 データベースで 510 文字より長く ANSI データをバインドする場合。 以下の 510 文字値では、実際の cbValue を返します。
