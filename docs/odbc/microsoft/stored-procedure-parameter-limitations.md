---
title: "ストアド プロシージャ パラメーターの制限事項 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- stored procedures [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], stored procedures
ms.assetid: 8b804bcf-4cce-4e6f-aa45-00bab9ef9921
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0adaba03f6de2e0dc8ae91fa2035b81ed50b2618
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="stored-procedure-parameter-limitations"></a>ストアド プロシージャのパラメーターの制限
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 10 を使用するプロシージャが格納されている Oracle を実行しているか、複数の出力パラメーター、アクセス違反や ActiveX データ オブジェクト (ADO) エラーの結果として得られるストアド プロシージャの呼び出しは失敗します。 これは、Microsoft ODBC Driver をバージョン 8.0.4.0.0 と Oracle クライアント ソフトウェアの 8.0.4.0.4 for Oracle を使用する場合に発生します。  
  
 問題を解決するには、Oracle クライアント ソフトウェアは、8.0.4.2.0 のバージョンにアップグレードまたはそれ以上でなければなりません。 詳細については、連絡先 Oracle Corporation、[パッチ](../../odbc/microsoft/oracle-software-patches.md)です。  
  
> [!NOTE]  
>  この問題は、Oracle クライアント ソフトウェア バージョン 8.0.3.0.0 の早期のリリースでは発生しません。
