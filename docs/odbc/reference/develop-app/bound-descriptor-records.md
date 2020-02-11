---
title: バインドされた記述子レコード |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- bound descriptor records [ODBC]
- descriptors [ODBC], bound descriptor records
ms.assetid: 55d09344-6682-40f6-b634-036b134ff650
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4d0016a2849feb5656cb3cd6dd46eff444f37058
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68118761"
---
# <a name="bound-descriptor-records"></a>バインドされた記述子レコード
アプリケーションが記述子レコードの SQL_DESC_DATA_PTR フィールドを設定して、そのレコードに null 値が含まれないようにすると、レコードは "*バインド*" と呼ばれます。  
  
 記述子が APD の場合、バインドされた各レコードはバインドされたパラメーターを構成します。 入力パラメーターの場合、アプリケーションは、ステートメントを実行する前に、SQL ステートメントの動的パラメーターマーカーごとにパラメーターをバインドする必要があります。 出力パラメーターの場合、アプリケーションでパラメーターをバインドする必要はありません。  
  
 記述子が、データベースデータの行を記述する場合は、バインドされた各レコードがバインド列を構成します。
