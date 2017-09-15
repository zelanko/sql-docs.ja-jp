---
title: "SQLInstallTranslator マッピング |Microsoft ドキュメント"
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
- SQLInstallTranslator function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLInstallTranslator
ms.assetid: bcd9ba4f-7834-4bc4-876e-c7478998e524
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 07308a2c737f2fbe6857d8a65a913f881b8e658f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlinstalltranslator-mapping"></a>SQLInstallTranslator マッピング
ODBC 2 時にします。*x*アプリケーション呼び出し**SQLInstallTranslator**から ODBC 3*.x*ドライバー、ドライバー マネージャーは、マップの呼び出し**SQLInstallTranslatorEx**.アプリケーションを呼び出せません**SQLInstallTranslator** ODBC 3*.x*ドライバー マネージャーで、 *lpszInfFile*引数が NULL 以外の値に設定します。 ODBC です。ODBC 2 で使用される INF ファイル。*x* ODBC 3 ではサポートされなく*.x*旧バージョンとの互換性のためにあっても、します。
