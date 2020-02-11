---
title: スレッドを作成して終了する |Microsoft Docs
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
ms.openlocfilehash: b97f29ad06c4ed961f3cee571b0ca7b8d9c0b774
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68002084"
---
# <a name="creating-and-terminating-threads"></a>スレッドの作成と終了
ODBC を使用するマルチスレッドアプリケーションでは、Microsoft® Visual C++®ランタイムライブラリ関数 **_beginthread**および **_endthread** (または **_beginthreadex**と **_Endthreadex**) を呼び出して、odbc ドライバーマネージャーを呼び出すスレッドを作成および終了する必要があります。 アプリケーションが Microsoft Windows NT® functions **CreateThread**と**EndThread**を呼び出すと、ドライバーマネージャーと一部の ODBC ドライバーが**CreateThread**を呼び出すことによって作成されたスレッドで動作しない C ランタイム関数を呼び出すため、メモリリークが発生します。 詳細については、Microsoft Windows®のドキュメントを参照してください。
