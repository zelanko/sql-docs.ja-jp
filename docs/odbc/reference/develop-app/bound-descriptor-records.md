---
title: バインドされた記述子レコード |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- bound descriptor records [ODBC]
- descriptors [ODBC], bound descriptor records
ms.assetid: 55d09344-6682-40f6-b634-036b134ff650
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: acb8d22cc7d2af1efca121c70e99137df88f282b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="bound-descriptor-records"></a>バインドされた記述子レコード
アプリケーションは、null 値が含まれないように、記述子レコードの SQL_DESC_DATA_PTR フィールドを設定、レコードがあると言います。*バインド*です。  
  
 記述子が、APD の場合は、バインドされた各レコードは、バインドされたパラメーターを構成します。 入力パラメーターは、アプリケーションは、ステートメントを実行する前に SQL ステートメントで各動的パラメーター マーカーにパラメーターをバインドする必要があります。 出力パラメーター、アプリケーションは、パラメーターをバインドできません必要があります。  
  
 記述子は、ARD では、データベースのデータの行を記述するには、バインドされた各レコードは、バインドされた列を構成します。
