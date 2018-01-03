---
title: "Hardware and Software Requirements (ODBC) |Microsoft ドキュメント"
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
helpviewer_keywords:
- hardware requirements [ODBC], desktop database drivers
- software requirements [ODBC], desktop database drivers
- system requirements [ODBC], desktop database drivers
- requirements [ODBC], desktop database drivers
ms.assetid: 6df2e9cd-de10-4629-97bd-32f2782616c7
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7cee0668d49ba0edb88d21799ec571aa708259dd
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="hardware-and-software-requirements-odbc"></a>Hardware and Software Requirements (ODBC)
このトピックでは、デスクトップの ODBC データベース ドライバーを使用するための要件を示します。  
  
## <a name="hardware-requirements"></a>ハードウェア要件  
 使用するには、ODBC のデスクトップ データベース ドライバーが必要です。  
  
-   IBM と互換性のあるパーソナル コンピューターの場合は。  
  
-   6 MB の空きディスク領域のハード_ディスク。  
  
-   16 MB 以上のランダム アクセス メモリ (RAM)。  
  
## <a name="software-requirements"></a>ソフトウェア要件  
 ODBC ドライバーを使用してデータにアクセスするには、次が必要です。  
  
-   ODBC ドライバー。  
  
-   32 ビット ODBC ドライバー マネージャー、3.51 または後 (Odbc32.dll) です。  
  
-   Microsoft Windows 95 以降または Windows NT 4.0 および Windows 2000 です。  
  
-   Microsoft ODBC driver を使用してアプリケーションを少なくとも 20 KB のスタック サイズ。  
  
 Microsoft Windows NT 4.0 または Windows 2000 を使用する場合、32 ビット ドライバーはスレッド セーフ ドライバーへのアクセスを制御するグローバル セマフォを使用してのみです。 ドライバーの同時使用は非常に限定 Windows NT でします。 Jet ISAM レイヤーに対するすべてのアクセスは、Microsoft Jet エンジンを使用するすべてのアプリケーションにシングル スレッドになります。  
  
 を Windows on Windows (WOW) Microsoft Windows NT 4.0 上で複数の 16 ビット アプリケーションを実行する場合は、別のメモリ領域で、アプリケーションを実行する必要があります。 (同じメモリ領域は使えません ODBC では、同じプロセス内の複数の環境がサポートされていません。)で別のメモリ領域を、アプリケーションを実行するアイコンを選択、アプリケーションのプログラム マネージャーで、開く、**ファイル**メニューをクリック**プロパティ**、クリックして**個別のメモリを実行領域**です。  
  
 Windows 95 で 16 ビット アプリケーションでこれらのドライバーの使用はサポートされていません。  
  
## <a name="driver-specific-hardware-and-software-requirements"></a>ドライバー固有のハードウェアとソフトウェアの要件  
  
-   Access および dBASEdrivers autoexec.bat ファイルや Config.sys ファイルの変更があります。
