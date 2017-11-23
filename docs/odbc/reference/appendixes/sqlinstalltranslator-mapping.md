---
title: "SQLInstallTranslator マッピング |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLInstallTranslator function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLInstallTranslator
ms.assetid: bcd9ba4f-7834-4bc4-876e-c7478998e524
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cb17f3d77b39c43d1f20c4598ac0192332a9cf13
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="sqlinstalltranslator-mapping"></a>SQLInstallTranslator マッピング
ODBC 2 時にします。*x*アプリケーション呼び出し**SQLInstallTranslator**から ODBC 3*.x*ドライバー、ドライバー マネージャーは、マップの呼び出し**SQLInstallTranslatorEx**.アプリケーションを呼び出せません**SQLInstallTranslator** ODBC 3*.x*ドライバー マネージャーで、 *lpszInfFile*引数が NULL 以外の値に設定します。 ODBC です。ODBC 2 で使用される INF ファイル。*x* ODBC 3 ではサポートされなく*.x*旧バージョンとの互換性のためにあっても、します。
