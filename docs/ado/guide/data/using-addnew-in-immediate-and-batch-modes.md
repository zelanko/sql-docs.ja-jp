---
title: "イミディ エイト AddNew とバッチ モードを使用して |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AddNew method [ADO]
- ADO, editing data
- ADO, adding data
- editing data [ADO], AddNew method
ms.assetid: ed314bb9-e188-4658-a68c-a2abc49610be
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 27ad77c8e5b9213dd8cc0243bec5d9ea8dd54ed4
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="using-addnew-in-immediate-and-batch-modes"></a>イミディ エイト AddNew とバッチ モードを使用してください。
動作、 **AddNew**メソッドは、の更新モードによって異なります、 **Recordset**オブジェクトとするかどうかを渡す、 *FieldList*と*値*引数。  
  
 即時更新モードで (をプロバイダーに変更を書き込みます、基になるデータ ソースを呼び出すと、**更新**メソッド) を呼び出す、 **AddNew**メソッドの引数を設定せず、 **EditMode**プロパティを**adEditAdd です。** プロバイダーは、ローカルでフィールド値の変更をキャッシュします。 呼び出す、**更新**メソッドは、データベースに新しいレコードをポストし、リセット、 **EditMode**プロパティを**adEditNone です。** 渡す場合、 *FieldList*と*値*引数、ADO はすぐに、新しいレコードをデータベースにポスト (ありません**更新**呼び出しが必要) 以外の場合は、 **EditMode**プロパティの値は変更されません (**adEditNone**)。  
  
 バッチ更新モードでの呼び出し、 **AddNew**メソッドの引数を設定せず、 **EditMode**プロパティを**adEditAdd**です。 プロバイダーは、ローカルでフィールド値の変更をキャッシュします。 呼び出す、**更新**メソッドは、現在、新しいレコードを追加**レコード セット**をリセットし、 **EditMode**プロパティを**adEditNone**が、呼び出されるまで、プロバイダーが、基になるデータベースへの変更を通知できません、 **UpdateBatch**メソッドです。 渡す場合、 *FieldList*と*値*引数、ADO の記憶域のキャッシュ プロバイダーに新しいレコードを送信する以外の場合を呼び出す必要があります、 **UpdateBatch**新しいを投稿する方法基になるデータベースに記録します。 詳細については**更新**と**UpdateBatch**を参照してください[更新およびデータの永続化](../../../ado/guide/data/updating-and-persisting-data.md)です。
