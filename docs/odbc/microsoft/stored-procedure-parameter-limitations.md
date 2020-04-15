---
title: ストアド プロシージャ パラメータの制限 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], stored procedures
ms.assetid: 8b804bcf-4cce-4e6f-aa45-00bab9ef9921
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bbd748884575791d5f170e95bc5aa465b61624b7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299202"
---
# <a name="stored-procedure-parameter-limitations"></a>ストアド プロシージャのパラメーターの制限
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 10 以上の出力パラメータを使用する Oracle ストアド プロシージャを実行すると、ストアド プロシージャの呼び出しが失敗し、アクセス違反または ActiveX データ オブジェクト (ADO) エラーが発生します。 この問題は、Oracle クライアント ソフトウェアのバージョン 8.0.4.0.0 および 8.0.4.0.4 で Oracle 用 Microsoft ODBC ドライバーを使用している場合に発生する可能性があります。  
  
 この問題を解決するには、Oracle クライアント ソフトウェアをバージョン 8.0.4.2.0 以降にアップグレードする必要があります。 [更新プログラム](../../odbc/microsoft/oracle-software-patches.md)の詳細については、Oracle社にお問い合わせください。  
  
> [!NOTE]  
>  この問題は、Oracle クライアント ソフトウェア バージョン 8.0.3.0.0 の初期リリースでは発生しません。
