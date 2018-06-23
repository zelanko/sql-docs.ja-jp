---
title: 変更をキャプチャするために選択したテーブルに対する変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- makChanToTab
ms.assetid: a309f82a-c6ef-464d-a6ef-df555bfb609a
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 5d6399a9d1651c789899cc84b1afe8b1e053ba9e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36073062"
---
# <a name="make-changes-to-the-tables-selected-for-capturing-changes"></a>変更をキャプチャするために選択したテーブルに対する変更
  このダイアログ ボックスでは、選択したテーブルから変更をキャプチャする特定の列を選択できます。 **[セキュリティ ロール]** と **[キャプチャ インスタンス]** の情報を編集することもできます。  
  
 このダイアログ ボックスでは、変更をキャプチャするために選択したテーブルに次の変更を加えることができます。  
  
 **CDC インスタンスに含める列の変更**  
  
 次のいずれかまたは両方の操作を行います。  
  
-   CDC インスタンスに含める追加の列の横のチェック ボックスをオンにします。  
  
-   CDC インスタンスに含めない列の横のチェック ボックスをオフにします。  
  
 **特定の列のデータ型の変更**  
  
 特定の列に別のデータ型を選択することができます。 元のデータ型と互換性のあるデータ型への変更のみが可能です。  
  
 データ型を変更するには、 **[データ型]** 列をクリックし、別のデータ型を選択します。 元のデータ型と互換性のあるデータ型のみを選択できます。  
  
> [!NOTE]  
>  他に選択できるデータ型がない場合は、ドロップダウン リストが表示されません。  
  
 **セキュリティ ロールの変更**  
  
 **"セキュリティ ロール"** フィールドで、セキュリティ ゲーティング ロールの新しい名前を入力するか、既存の名前を編集します。  
  
 **キャプチャ インスタンスの変更または追加**  
  
 **"キャプチャ インスタンス"** フィールドに、キャプチャ インスタンスの名前を入力します。  
  
## <a name="see-also"></a>参照  
 [SQL Server 変更データベース インスタンスを作成する方法](how-to-create-the-sql-server-change-database-instance.md)   
 [Oracle のテーブルおよび列の選択](select-oracle-tables-and-columns.md)  
  
  