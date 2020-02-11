---
title: プロシージャ呼び出しのパラメーターマーカー |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- parameter markers [ODBC]
- interoperability of SQL statements [ODBC], parameter markers
ms.assetid: cda56f2b-6eec-4cbc-8dbb-36d8fa9f9216
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3bb24fb628e9e49fd94104af05217511a8f57c3e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67912314"
---
# <a name="parameter-markers-in-procedure-calls"></a>プロシージャ呼び出しのパラメーター マーカー
パラメーターを受け取るプロシージャを呼び出す場合、相互運用可能なアプリケーションでは、リテラルパラメーター値ではなくパラメーターマーカーを使用する必要があります。 一部のデータソースでは、プロシージャ呼び出しでのリテラルパラメーター値の使用はサポートされていません。 パラメーターの詳細については、「[ステートメントパラメーター](../../../odbc/reference/develop-app/statement-parameters.md)」を参照してください。 プロシージャの呼び出しの詳細については、このセクションで後述する「[プロシージャ呼び出し](../../../odbc/reference/develop-app/procedure-calls.md)」を参照してください。
