---
title: デスクトップ データベース ドライバの履歴 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], history
- ODBC desktop database drivers [ODBC], history
- desktop database drivers [ODBC], history
ms.assetid: b4a2aff8-bde7-4bd5-8580-bc50f27311c8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 89434b397c07fdee751ca4272b65ac2eada94cf3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304983"
---
# <a name="history-of-the-desktop-database-drivers"></a>デスクトップ データベース ドライバーの履歴
次の表は、デスクトップ データベース ドライバーのバージョン履歴を示しています。  
  
|Version|リリース日|説明|  
|-------------|------------------|-----------------|  
|1.0|1993年8月|PageAhead ソフトウェアによって生成された SIMBA クエリ プロセッサを使用しました。 SIMBA は ODBC 呼び出しと SQL ステートメントを受信し、それらを Microsoft Jet インストール可能な ISAM 呼び出しに処理した後、適切なインストール可能な ISAM ドライバを読み込んで呼び出すために、Microsoft Jet ISAM ディスパッチ レイヤを呼び出しました。|  
|2.0|1994年12月|ODBC 2.0 で使用され、ODBC 機能が大幅に拡張されました。 バージョン 2.0 の大きな変更は、Microsoft Jet データベース エンジンが SIMBA クエリ プロセッサを置き換えたというものでした。 Microsoft Jet データベース エンジンを使用すると、デスクトップ データベース ドライバは、インストール可能な ISAM ドライバおよびマイクロソフト アクセス テクノロジと緊密に統合されました。 重要な機能強化は次のとおりです。<br /><br /> - スクロール可能なカーソルのネイティブサポート。<br />- 外部結合、更新可能および異種結合、およびトランザクションに対するネイティブサポート。<br />- 32 ビット 版のドライバを使用します。|  
|3.0|1995年10月|Windows 95 および Windows NT ワークステーションまたは NT サーバー 3.51 のサポートを提供しました。 このリリースには 32 ビット ドライバーのみが含まれていました。Windows バージョン 3.1 用の 16 ビット ドライバは削除されました。|  
|3.5|1996年10月|これらのドライバは、2 バイト文字セット (DBCS) が有効で、以前のバージョンよりもインターネット アプリケーションでの使用に適しており、ファイル データ ソース名 (DSN) の使用に対応していました。 マイクロソフト のアクセス ドライバーは、Windows 95/98 および Windows NT 3.51 以降のオペレーティング システム用の Alpha プラットフォームで使用する RISC バージョンでリリースされました。|  
|4.0|1998年後半|以前のバージョンの ANSI 形式と互換性を持つマイクロソフトの Jet エンジン Unicode 形式のサポートを提供します。|  
  
> [!NOTE]  
>  バージョン 3.5 のドライバは、ODBC2 で動作するように設計されています。*x .* ODBC 3.0 でも動作しますが、ODBC 3.0 のすべての機能をサポートしているわけではありません。 ODBC 3.0 でこれらのドライバがどのように動作するかについては、「[下位互換性と標準準拠](../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md)」を参照してください。
