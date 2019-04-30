---
title: ストアド プロシージャ パラメーターの制限事項 |Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7dc74811bf6cead91850ebd3fcaa8cf64025c80d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63270854"
---
# <a name="stored-procedure-parameter-limitations"></a>ストアド プロシージャのパラメーターの制限
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 10 を使用するプロシージャが格納されている Oracle を実行しているか、複数の出力パラメーター、アクセス違反または ActiveX Data Objects (ADO) エラーが発生、ストアド プロシージャの呼び出しは失敗します。 これは、Microsoft ODBC Driver をバージョン 8.0.4.0.0 と、Oracle クライアント ソフトウェアの 8.0.4.0.4 for Oracle を使用する場合に発生します。  
  
 問題を修正するには、Oracle クライアント ソフトウェアは、8.0.4.2.0 バージョンにアップグレードするまたは上位になければなりません。 詳細については、連絡先 Oracle Corporation、[パッチ](../../odbc/microsoft/oracle-software-patches.md)します。  
  
> [!NOTE]  
>  この問題は、Oracle クライアント ソフトウェア version 8.0.3.0.0 の初期リリースでは発生しません。
