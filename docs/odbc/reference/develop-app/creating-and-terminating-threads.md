---
title: スレッドの作成と終了 |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3536deef604d7dbf645903e7d171a58cd9fec96a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301693"
---
# <a name="creating-and-terminating-threads"></a>スレッドの作成と終了
ODBC を使用するマルチスレッド アプリケーションでは®、odbc ドライバー マネージャーを呼び出すスレッドを**作成および終了**する_endthread (または **_beginthreadex**と **_endthreadex)** を **_beginthread**して Visual C++® ランタイム ライブラリ関数を呼び出す必要があります。 アプリケーションが代わりに Microsoft Windows NT® 関数**CreateThread**と**EndThread**を呼び出すと、ドライバー マネージャーと一部の ODBC ドライバーが **、CreateThread**を呼び出すことによって作成されたスレッドでは動作しない C ランタイム関数を呼び出すため、メモリ リークが発生します。 詳細については、Windows® のドキュメントを参照してください。
