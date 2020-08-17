---
description: ストアド プロシージャのパラメーターの制限
title: ストアドプロシージャパラメーターの制限 |Microsoft Docs
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
ms.openlocfilehash: be3f28c748f1322c3557c1030e2fb79b12db399b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88339598"
---
# <a name="stored-procedure-parameter-limitations"></a>ストアド プロシージャのパラメーターの制限
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows では削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用してください。  
  
 10個以上の出力パラメーターを使用する Oracle ストアドプロシージャを実行すると、ストアドプロシージャの呼び出しは失敗し、アクセス違反または ActiveX データオブジェクト (ADO) エラーが発生します。 これは、Microsoft ODBC Driver for Oracle と、Oracle クライアントソフトウェアのバージョン8.0.4.0.0 および8.0.4.0.4 を使用する場合に発生する可能性があります。  
  
 この問題を解決するには、Oracle クライアントソフトウェアをバージョン8.0.4.2.0 以上にアップグレードする必要があります。 [修正プログラム](../../odbc/microsoft/oracle-software-patches.md)の詳細については、Oracle Corporation にお問い合わせください。  
  
> [!NOTE]  
>  この問題は、Oracle クライアントソフトウェアバージョン8.0.3.0.0 の初期リリースでは発生しません。
