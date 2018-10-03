---
title: 作成して、スレッドの終了 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- terminating threads [ODBC]
- threads [ODBC]
- multithreaded applications [ODBC]
ms.assetid: a2cf98ef-1c71-4742-8ee2-b53fd8e04333
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e9d6d15c449d88043e844addd12ac10a98d5c4a0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47722380"
---
# <a name="creating-and-terminating-threads"></a>スレッドの作成と終了
ODBC を使用するマルチ スレッド アプリケーションは、Microsoft® Visual C++® ランタイム ライブラリ関数を呼び出す必要があります **_beginthread**と **_endthread** (または **_beginthreadex**と **_endthreadex**) を作成して、ODBC ドライバー マネージャーを呼び出すスレッドを終了します。 アプリケーションが Microsoft Windows NT® 関数を呼び出す場合**CreateThread**と**EndThread**代わりに、ドライバー マネージャーと一部の ODBC ドライバーは、C ランタイムを呼び出すため、リークが発生するメモリ関数呼び出すことによって作成されたスレッドでは機能しません**CreateThread**します。 詳細については、Microsoft Windows® ドキュメントを参照してください。
