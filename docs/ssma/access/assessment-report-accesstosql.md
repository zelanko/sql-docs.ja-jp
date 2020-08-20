---
description: 評価レポート (Sql server による)
title: 評価レポート (Sql server による) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Assessment Report dialog box
- Conversion Report dialog box
ms.assetid: ba6f53aa-0049-4c49-8bb8-607a8bfaa737
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 5f1058947591fdd454ce181b2d098f88b183cbe1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88497828"
---
# <a name="assessment-report-accesstosql"></a>評価レポート (Sql server による)
[評価レポート] ウィンドウには、データベースオブジェクトを構文に変換した結果が表示され [!INCLUDE[tsql](../../includes/tsql-md.md)] ます。また、移行プロジェクトの複雑さとコストを見積もるのにも役立ちます。  
  
評価レポートを作成するには、ソースメタデータエクスプローラーで変換するオブジェクトを選択し、[ **データベース**] を右クリックして、[ **レポートの作成**] を選択します。 スキーマを変換した後に、このレポートを自動的に表示することもできます。 ただし、レポート名は変換レポートになります。 詳細については、「 [プロジェクトの設定 (GUI) (SSMA Common)](https://msdn.microsoft.com/cf06baf1-8714-48a3-95dc-781f6ca53693)」を参照してください。  
  
## <a name="options"></a>オプション  
**エクスプローラー ペイン**  
評価レポートのオブジェクトの階層が含まれます。 [フォルダー] を展開して、個々のオブジェクトとサブコンポーネントを表示します。 カテゴリまたはオブジェクトをクリックすると、そのカテゴリまたはオブジェクトの変換統計が詳細ウィンドウに表示されます。  
  
**詳細ウィンドウ**  
選択したオブジェクトの変換の統計情報またはエラーと警告メッセージを表示します。 たとえば、[テーブル] フォルダーを選択した場合、[詳細] ペインには、変換された外部キー、インデックス、主キー、およびテーブルの数が表示されます。  
  
**メッセージ ペイン (Messages pane)**  
評価レポートの作成時に生成されたエラー、警告、および情報メッセージを表示します。 メッセージは数値でグループ化されます。  
  
メッセージの詳細を表示するには、[ **エラー**]、[ **警告**]、または [ **メッセージ**] をクリックし、メッセージを展開します。 SSMA には、このエラーが発生したオブジェクトの一覧が表示されます。 オブジェクトをクリックすると、そのオブジェクトのすべての変換の詳細が表示されます。  
  
## <a name="see-also"></a>関連項目  
[ユーザーインターフェイスリファレンス (アクセス)](https://msdn.microsoft.com/af24c303-4a41-449b-9c86-d6558a97e839)  
  
