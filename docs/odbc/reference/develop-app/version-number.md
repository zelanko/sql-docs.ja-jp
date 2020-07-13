---
title: バージョン番号 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- version number supported [ODBC]
- interoperability [ODBC], version number supported
ms.assetid: 6eccacdf-b837-4b66-bd48-ba31771acecb
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 37b7924380b9e9beb60792b50436eaa13a503c76
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306720"
---
# <a name="version-number"></a>バージョン番号
ODBC には、それぞれ機能が異なる複数のバージョンがあります。 アプリケーションでは、SQL_ODBC_VER オプションと SQL_DRIVER_ODBC_VER オプションを指定して**SQLGetInfo**を呼び出すことによって、ドライバーマネージャーと特定のドライバーがサポートする ODBC バージョンを決定します。
