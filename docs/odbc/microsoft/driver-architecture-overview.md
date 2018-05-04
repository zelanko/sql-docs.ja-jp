---
title: ドライバーのアーキテクチャの概要 |Microsoft ドキュメント
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
- Visual FoxPro ODBC driver [ODBC], architecture
- FoxPro ODBC driver [ODBC], architecture
ms.assetid: ef5a91cd-158e-40bf-b5a8-8ba535c4705e
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0f9c5d4720e126c6d496754201889b862b508e90
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="driver-architecture-overview"></a>ドライバーのアーキテクチャの概要
Microsoft Visual FoxPro ODBC ドライバーは、32 ビット ドライバーを開き、Microsoft Visual FoxPro データベースまたは開く Database Connectivity (ODBC) インターフェイスを使用して FoxPro テーブルをクエリすることができます。 FoxPro を次の種類のアプリケーションを使用してデータにアクセスすることができます。  
  
-   Microsoft Excel や Microsoft Word などの Microsoft Office アプリケーションを Microsoft クエリを使用する ODBC と通信します。  
  
-   Microsoft Visual C または ODBC SDK API を使用する C で記述されたアプリケーション。  
  
-   Microsoft Visual Basic または Microsoft Visual Basic for Applications で記述されたアプリケーション。  
  
 各ケースでは、情報の要求は、ODBC API を使用します。 ODBC ドライバー マネージャーが開き、FoxPro テーブルおよびデータベースからデータを取得する Visual FoxPro ODBC ドライバーでは動作します。  
  
 アーキテクチャは、次の図で表されます。  
  
 ![ODBC ドライバーのアーキテクチャを示しています](../../odbc/microsoft/media/vfparch.gif "vfparch。")  
  
 このセクションでは、次のトピックを扱います。  
  
-   [Visual FoxPro 用語集](../../odbc/microsoft/visual-foxpro-terminology.md)  
  
-   [インストールして、Visual FoxPro ODBC ドライバーを構成します。](../../odbc/microsoft/installing-and-configuring.md)  
  
-   [Visual FoxPro ODBC ドライバーの使用](../../odbc/microsoft/using-the-visual-foxpro-odbc-driver.md)
