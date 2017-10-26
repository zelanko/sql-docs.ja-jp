---
title: "デスクトップ データベース ドライバーの履歴 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], history
- ODBC desktop database drivers [ODBC], history
- desktop database drivers [ODBC], history
ms.assetid: b4a2aff8-bde7-4bd5-8580-bc50f27311c8
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f6876496d243cefd2f3d6b7eb0cd5480bf225189
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="history-of-the-desktop-database-drivers"></a>デスクトップ データベース ドライバーの履歴
次の表は、デスクトップ データベース ドライバーのバージョン履歴を表示します。  
  
|バージョン|リリース日|Description|  
|-------------|------------------|-----------------|  
|1.0|年 8 月 1993|PageAhead ソフトウェアによって生成される SIMBA クエリ プロセッサを使用します。 SIMBA は、ODBC 呼び出しと SQL ステートメントを受信するには、Microsoft Jet インストール可能な ISAM 呼び出しにそれらを処理し、Microsoft Jet ISAM ディスパッチ レイヤーをロードし、インストール可能な ISAM に適したドライバーを呼び出すと呼ばれます。|  
|2.0|1994 年 12 月|ODBC の機能を大幅に拡張する ODBC 2.0 と共に使用します。 バージョン 2.0 では、重大な変更は、Microsoft Jet データベース エンジンに SIMBA クエリ プロセッサが置き換えられたことでした。 Microsoft Jet データベース エンジンとデスクトップ データベース ドライバーは ISAM ドライバーのインストール可能な Microsoft Jet および Microsoft Access 技術とより緊密に統合します。 多くの機能強化は次のとおりです。<br /><br /> -スクロール可能なカーソルのネイティブ サポート。<br />-外部結合、および更新可能な異種結合、およびトランザクションのネイティブ サポート。<br />32 ビット バージョンの Microsoft Windows NT のドライバーです。|  
|3.0|1995 年 10 月|Windows 95 および Windows NT ワークステーションまたはサーバーのサポートを提供します。 このリリースに含まれていたのみの 32 ビット ドライバーWindows バージョン 3.1 用の 16 ビット ドライバーが削除されました。|  
|3.5|1996 年 10 月|これらのドライバーが 2 バイト文字セット (DBCS)-有効になっているがより適してインターネット アプリケーションで使用するより以前のバージョン、およびファイル データ ソース名 (Dsn) の使用に対応します。 Microsoft Access ドライバーは、Windows 95/98 および Windows NT 3.51 以降のオペレーティング システムに対して Alpha プラットフォームで使用する RISC バージョンでリリースされました。|  
|4.0|1998 年の終わり|以前のバージョンの ANSI 形式の互換性と Microsoft Jet エンジン Unicode 形式のサポートを提供します。|  
  
> [!NOTE]  
>  Version3.5 ドライバーは、ODBC2 を使用する設計されました。*x*です。 ODBC 3.0 では機能しますが、また、ODBC 3.0 のすべての機能はサポートしていません。 これらのドライバーが ODBC 3.0 を操作する方法の詳細については、次を参照してください。[旧バージョンとの互換性と標準の順守](../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md)です。

