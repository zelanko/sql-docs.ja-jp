---
title: ドライバーのアーキテクチャの概要 |Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303463"
---
# <a name="driver-architecture-overview"></a>ドライバーのアーキテクチャの概要
Microsoft Visual FoxPro ODBC ドライバーは、Open Database Connectivity (ODBC) インターフェイスを使用して Microsoft Visual FoxPro データベースまたは FoxPro テーブルを開き、クエリを実行できるようにする32ビットドライバーです。 次の種類のアプリケーションを使用して、FoxPro データにアクセスできます。  
  
-   Microsoft Query を使用して ODBC と通信する、Microsoft Excel、microsoft Word などの Microsoft Office アプリケーション。  
  
-   ODBC SDK API を使用する Microsoft Visual C++ または C で記述されたアプリケーション。  
  
-   Microsoft Visual Basic または Microsoft Visual Basic for Applications で記述されたアプリケーション。  
  
 いずれの場合も、情報の要求では ODBC API が使用されます。 ODBC ドライバーマネージャーは、Visual FoxPro ODBC ドライバーと連携して、FoxPro テーブルおよびデータベースからデータを開いたり取得したりします。  
  
 アーキテクチャは、次の図で表されています。  
  
 ![ODBC ドライバーのアーキテクチャを示します。](../../odbc/microsoft/media/vfparch.gif "vfparch")  
  
 このセクションでは、次のトピックを扱います。  
  
-   [Visual FoxPro 用語集](../../odbc/microsoft/visual-foxpro-terminology.md)  
  
-   [Visual FoxPro ODBC ドライバーのインストールと構成](../../odbc/microsoft/installing-and-configuring.md)  
  
-   [Visual FoxPro ODBC ドライバーの使用](../../odbc/microsoft/using-the-visual-foxpro-odbc-driver.md)
