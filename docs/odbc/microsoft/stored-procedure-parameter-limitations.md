---
title: ストアド プロシージャ パラメーターの制限事項 |Microsoft ドキュメント
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
- stored procedures [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], stored procedures
ms.assetid: 8b804bcf-4cce-4e6f-aa45-00bab9ef9921
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 34f3bc435a0bbd514eed4f9ce6100a9cca6b6cb7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="stored-procedure-parameter-limitations"></a>ストアド プロシージャのパラメーターの制限
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 10 を使用するプロシージャが格納されている Oracle を実行しているか、複数の出力パラメーター、アクセス違反や ActiveX データ オブジェクト (ADO) エラーの結果として得られるストアド プロシージャの呼び出しは失敗します。 これは、Microsoft ODBC Driver をバージョン 8.0.4.0.0 と Oracle クライアント ソフトウェアの 8.0.4.0.4 for Oracle を使用する場合に発生します。  
  
 問題を解決するには、Oracle クライアント ソフトウェアは、8.0.4.2.0 のバージョンにアップグレードまたはそれ以上でなければなりません。 詳細については、連絡先 Oracle Corporation、[パッチ](../../odbc/microsoft/oracle-software-patches.md)です。  
  
> [!NOTE]  
>  この問題は、Oracle クライアント ソフトウェア バージョン 8.0.3.0.0 の早期のリリースでは発生しません。
