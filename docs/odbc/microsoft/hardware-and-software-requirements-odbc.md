---
title: ハードウェアおよびソフトウェアの要件 (ODBC) |マイクロソフトドキュメント
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81295242"
---
# <a name="hardware-and-software-requirements-odbc"></a>ハードウェアとソフトウェアの要件 (ODBC)
このトピックでは、ODBC デスクトップ データベース ドライバーを使用するための要件を示します。  
  
## <a name="hardware-requirements"></a>ハードウェア要件  
 ODBC デスクトップ データベース ドライバを使用するには、次の機能が必要です。  
  
-   IBM 互換のパーソナル・コンピューター。  
  
-   6 MB の空きディスク領域を持つハード ディスク。  
  
-   ランダム アクセス メモリ (RAM) の少なくとも 16 MB。  
  
## <a name="software-requirements"></a>ソフトウェア要件  
 ODBC ドライバを使用してデータにアクセスするには、次の条件が必要です。  
  
-   ODBC ドライバ。  
  
-   32 ビット ODBC ドライバー マネージャー、バージョン 3.51 以降 (Odbc32.dll)。  
  
-   Windows 95 以降、または Windows NT 4.0 または Windows 2000。  
  
-   Microsoft ODBC ドライバを使用するアプリケーションのスタック サイズが 20 KB 以上です。  
  
 Microsoft Windows NT 4.0 または Windows 2000 を使用する場合、32 ビット ドライバはスレッド セーフですが、ドライバへのアクセスを制御するグローバル セマフォを使用する場合に限られます。 ドライバの同時使用は、Windows NT では非常に限られています。 Jet ISAM レイヤへのすべてのアクセスは、Microsoft Jet エンジンを使用するすべてのアプリケーションに対してシングルスレッド化されます。  
  
 Windows NT 4.0 で Windows 上で複数の 16 ビット アプリケーションを実行する場合は、アプリケーションを別のメモリ領域で実行する必要があります。 (ODBC は同じプロセス内の複数の環境をサポートしていないため、同じメモリ領域を使用できません。アプリケーションを別のメモリ領域で実行するには、プログラム マネージャでアプリケーションのアイコンを選択し、[**ファイル**] メニューの [**プロパティ**] を**クリックします**。  
  
 Windows 95 で 16 ビット アプリケーションでこれらのドライバーを使用することはサポートされていません。  
  
## <a name="driver-specific-hardware-and-software-requirements"></a>ドライバ固有のハードウェアおよびソフトウェア要件  
  
-   アクセスおよび dBASEdrivers は、Autoexec.bat ファイルまたは Config.sys ファイルの変更を必要とする場合があります。
