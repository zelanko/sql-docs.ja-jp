---
title: バインドされた記述子レコード |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 155ef4951abddc7a73d9d4abfbc45248f33d653c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306309"
---
# <a name="bound-descriptor-records"></a>バインドされた記述子レコード
アプリケーションが記述子レコードのSQL_DESC_DATA_PTRフィールドを設定して、NULL 値が含まないようにすると、そのレコードは バインドされていると言*います*。  
  
 記述子が APD の場合、バインドされた各レコードは、バインドされたパラメーターを構成します。 入力パラメーターの場合、アプリケーションは、ステートメントを実行する前に、SQL ステートメント内の各動的パラメーター・マーカーのパラメーターをバインドする必要があります。 出力パラメーターの場合、アプリケーションはパラメーターをバインドする必要はありません。  
  
 記述子がデータベース・データの行を記述する ARD の場合、バインドされた各レコードはバインドされた列を構成します。
