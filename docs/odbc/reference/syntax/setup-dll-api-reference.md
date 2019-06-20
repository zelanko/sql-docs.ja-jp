---
title: セットアップ DLL API リファレンス |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], driver setup DLL
- driver setup DLL [ODBC]
ms.assetid: f9d03f17-1c0d-4e7c-9c04-8c316e07ef25
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d81bb9f5ec54f3d66089205f5b5941119d365501
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62652900"
---
# <a name="setup-dll-api-reference"></a>セットアップ DLL API リファレンス
このセクションは、ドライバーのセットアップ DLL API は、2 つの関数で構成の構文を説明します (**ConfigDriver**と**ConfigDSN**)。 **ConfigDriver**と**ConfigDSN**ドライバ DLL のいずれかを指定したり、別の DLL のセットアップします。  
  
 さらに、このセクションがトランスレーター セットアップ DLL API は、1 つの関数から成るの構文について説明します (**ConfigTranslator**)。 **ConfigTranslator**トランスレーター DLL のいずれかを指定したり、別の DLL のセットアップします。  
  
 各関数には、導入された ODBC のバージョンが付いています。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ConfigDriver 関数](../../../odbc/reference/syntax/configdriver-function.md)  
  
-   [ConfigDSN 関数](../../../odbc/reference/syntax/configdsn-function.md)  
  
-   [ConfigTranslator 関数](../../../odbc/reference/syntax/configtranslator-function.md)
