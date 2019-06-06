---
title: レコード セット関連のエラー情報 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Recordset-related errors [ADO]
- errors [ADO], Recordset-related
ms.assetid: 7e103574-59ad-4790-b5f9-fa8d715e711e
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: ef5f6cc4a262cecc81a8dd72f2d3e3f6a7e2fded
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66700414"
---
# <a name="recordset-related-error-information"></a>レコードセット関連のエラー情報
バッチの処理中に、**状態**のプロパティ、**レコード セット**オブジェクト内の個別のレコードに関する情報は、**レコード セット**します。 バッチ更新が実行する前に、**状態**のプロパティ、 **Recordset**追加、変更および削除するレコードについての情報が反映されます。 後**UpdateBatch**が呼び出されて、**状態**プロパティは、操作の成否を示します。 レコード間を移動すると、**レコード セット**の値、**状態**プロパティに対する変更を現在のレコードの状態を説明します。
