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
ms.topic: article
helpviewer_keywords:
- bound descriptor records [ODBC]
- descriptors [ODBC], bound descriptor records
ms.assetid: 55d09344-6682-40f6-b634-036b134ff650
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d1e7c9c3d93403515c118757a6a947a6b5a68b9c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="bound-descriptor-records"></a>バインドされた記述子レコード
アプリケーションは、null 値が含まれないように、記述子レコードの SQL_DESC_DATA_PTR フィールドを設定、レコードがあると言います。*バインド*です。  
  
 記述子が、APD の場合は、バインドされた各レコードは、バインドされたパラメーターを構成します。 入力パラメーターは、アプリケーションは、ステートメントを実行する前に SQL ステートメントで各動的パラメーター マーカーにパラメーターをバインドする必要があります。 出力パラメーター、アプリケーションは、パラメーターをバインドできません必要があります。  
  
 記述子は、ARD では、データベースのデータの行を記述するには、バインドされた各レコードは、バインドされた列を構成します。
