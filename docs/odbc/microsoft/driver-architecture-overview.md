---
title: ドライバアーキテクチャの概要 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], architecture
- FoxPro ODBC driver [ODBC], architecture
ms.assetid: ef5a91cd-158e-40bf-b5a8-8ba535c4705e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cd55290e09fbd35f5a1559ce4209693ef8eaaf73
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303463"
---
# <a name="driver-architecture-overview"></a>ドライバーのアーキテクチャの概要
Microsoft Visual FoxPro ODBC ドライバーは、開いているデータベース接続 (ODBC) インターフェイスを使用して、Microsoft ビジュアル FoxPro データベースまたは FoxPro テーブルを開いてクエリを実行できるようにする 32 ビット ドライバーです。 次の種類のアプリケーションを使用して FoxPro データにアクセスできます。  
  
-   クエリを使用して ODBC と通信する Excel や Word などの Office アプリケーション。  
  
-   ODBC SDK API を使用する Visual C++ または C で記述されたアプリケーション。  
  
-   アプリケーション用のマイクロソフトビジュアルベーシックまたはマイクロソフトの Visual Basic で記述されたアプリケーション。  
  
 いずれの場合も、情報の要求では ODBC API が使用されます。 ODBC ドライバー マネージャーは、開くし、FoxPro テーブルとデータベースからデータを取得するビジュアル フォックス プロ ODBC ドライバーと連携します。  
  
 アーキテクチャは次の図で表されます。  
  
 ![ODBC ドライバのアーキテクチャを示します。](../../odbc/microsoft/media/vfparch.gif "vfparch")  
  
 このセクションでは、次のトピックを扱います。  
  
-   [Visual FoxPro 用語集](../../odbc/microsoft/visual-foxpro-terminology.md)  
  
-   [ビジュアル フォックスプロ ODBC ドライバーのインストールと構成](../../odbc/microsoft/installing-and-configuring.md)  
  
-   [Visual FoxPro ODBC ドライバーの使用](../../odbc/microsoft/using-the-visual-foxpro-odbc-driver.md)
