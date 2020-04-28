---
title: ハードウェアとソフトウェアの要件 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- hardware requirements [ODBC], desktop database drivers
- software requirements [ODBC], desktop database drivers
- system requirements [ODBC], desktop database drivers
- requirements [ODBC], desktop database drivers
ms.assetid: 6df2e9cd-de10-4629-97bd-32f2782616c7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fe69775e379e9a9d661b4ddf81e577b738fcf34d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81295242"
---
# <a name="hardware-and-software-requirements-odbc"></a>ハードウェアとソフトウェアの要件 (ODBC)
このトピックでは、ODBC デスクトップデータベースドライバーを使用するための要件を示します。  
  
## <a name="hardware-requirements"></a>ハードウェア要件  
 ODBC デスクトップデータベースドライバーを使用するには、次のものが必要です。  
  
-   IBM と互換性のあるパーソナルコンピューター。  
  
-   6 MB の空きディスク領域があるハードディスク。  
  
-   16 MB 以上のランダムアクセスメモリ (RAM)。  
  
## <a name="software-requirements"></a>ソフトウェア要件  
 ODBC ドライバーを使用してデータにアクセスするには、次のものが必要です。  
  
-   ODBC ドライバー。  
  
-   32ビット ODBC ドライバーマネージャー、バージョン3.51 以降 (Odbc32.dll)。  
  
-   Microsoft Windows 95 以降、または Windows NT 4.0 または Windows 2000。  
  
-   Microsoft ODBC ドライバーを使用するアプリケーションでは、少なくとも 20 KB のスタックサイズ。  
  
 Microsoft Windows NT 4.0 または Windows 2000 を使用している場合、32ビットドライバーはスレッドセーフですが、ドライバーへのアクセスを制御するグローバルセマフォを使用することによってのみ使用されます。 ドライバーの同時使用は、Windows NT では非常に制限されています。 Jet ISAM レイヤーへのすべてのアクセスは、Microsoft Jet エンジンを使用しているすべてのアプリケーションに対してシングルスレッド化されます。  
  
 Microsoft Windows NT 4.0 で windows on windows (WOW) で複数の16ビットアプリケーションを実行する場合は、アプリケーションを別のメモリ領域で実行する必要があります。 (ODBC では同じプロセスで複数の環境がサポートされていないため、同じメモリ領域を使用することはできません)。アプリケーションを別のメモリ領域で実行するには、プログラムマネージャーでアプリケーションのアイコンを選択し、[**ファイル**] メニューを開き、[**プロパティ**] をクリックして、[**別のメモリ領域で実行**する] をクリックします。  
  
 Windows 95 では、16ビットアプリケーションによるこれらのドライバーの使用はサポートされていません。  
  
## <a name="driver-specific-hardware-and-software-requirements"></a>ドライバー固有のハードウェアとソフトウェアの要件  
  
-   Access および dBASEdrivers では、Autoexec.bat ファイルまたは config.sys ファイルの変更が必要になる場合があります。
