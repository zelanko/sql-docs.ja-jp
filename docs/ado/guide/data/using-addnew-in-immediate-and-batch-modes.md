---
title: イミディ エイト AddNew とバッチ モードの使用 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- AddNew method [ADO]
- ADO, editing data
- ADO, adding data
- editing data [ADO], AddNew method
ms.assetid: ed314bb9-e188-4658-a68c-a2abc49610be
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 7bcd9d42ef214d7b1a2a40d2f00eeba85f9399b7
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66704625"
---
# <a name="using-addnew-in-immediate-and-batch-modes"></a>イミディエイト モードとバッチ モードで AddNew を使用する
動作、 **AddNew**メソッドの更新モードによって異なります、 **Recordset**オブジェクトとかどうかを渡す、 *FieldList*と*値*引数。  
  
 即時更新モードで (これで、プロバイダーに変更を書き込みます、基になるデータ ソースを呼び出す、**更新**メソッド) を呼び出すと、 **AddNew**メソッドの引数を設定せず、 **EditMode**プロパティを**adEditAdd します。** プロバイダーは、ローカル フィールド値の変更をキャッシュします。 呼び出す、 **Update**メソッドは、データベースに新しいレコードをポストし、リセット、 **EditMode**プロパティを**adEditNone します。** 渡す場合、 *FieldList*と*値*引数、ADO はすぐに、新しいレコードをデータベースに投稿 (ありません**Update**呼び出しが必要)、 **EditMode**プロパティの値が変更されない (**adEditNone**)。  
  
 バッチ更新モードで呼び出して、 **AddNew**メソッドの引数を設定せず、 **EditMode**プロパティを**adEditAdd**。 プロバイダーは、ローカル フィールド値の変更をキャッシュします。 呼び出す、**更新**メソッドは、現在、新しいレコードを追加します**レコード セット**をリセットし、 **EditMode**プロパティを**adEditNone**が、呼び出すまで、プロバイダーが基になるデータベースへの変更を投稿できません、 **UpdateBatch**メソッド。 渡す場合、 *FieldList*と*値*引数、ADO の記憶域のキャッシュ プロバイダーに新しいレコードを送信する; を呼び出す必要があります、 **UpdateBatch**メソッドを新しい投稿基になるデータベースに記録します。 詳細については**Update**と**UpdateBatch**を参照してください[更新およびデータの永続化](../../../ado/guide/data/updating-and-persisting-data.md)します。
