---
title: レポートのプロパティ ダイアログ ボックスを参照 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- "10530"
- sql12.rtp.rptdesigner.reportproperties.references.f1
ms.assetid: 4639d368-9918-4bb1-9953-7a724ca78dea
caps.latest.revision: 39
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 8fc7bafa0a9cd0e292b5f697e94a781f21ca1844
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36075668"
---
# <a name="report-properties-dialog-box-references"></a>[参照] ([レポートのプロパティ] ダイアログ ボックス)
  **[レポートのプロパティ]** ダイアログ ボックスの **[参照]** を選択すると、レポート定義内の式で使用される、カスタム アセンブリまたは他の外部アセンブリ、およびカスタム クラスのインスタンスへの参照を追加または削除できます。  
  
## <a name="options"></a>および  
 **追加またはアセンブリを削除します。**  
 レポートで参照されるアセンブリを一覧表示します。 アセンブリは、レポートのデザインに使用するツールがインストールされているコンピューターおよびレポート サーバー上で使用できる必要があります。 参照の名前がの内容と一致する必要があります **\<CodeModule >** レポート定義言語 (.rdl) ファイル内にタグを正確にします。  
  
 **[追加]**  
 アセンブリを追加します。 参照ボタン ([...]) をクリックして **[開く]** ダイアログ ボックスを開き、レポートの処理および式の評価を実行するのに必要なアセンブリを選択します。  
  
 **Delete**  
 アセンブリの参照を一覧から削除するには、削除するアセンブリ名を選択し、 **[削除]** ボタンをクリックします。  
  
 **追加または削除するクラス**  
 レポートで使用されるクラスのインスタンスを一覧表示します。 クラスの一覧は、静的メンバーではなく、インスタンス ベースのメンバーでのみ使用されます。  
  
 **[追加]**  
 クラスの参照を追加します。 参照ボタン ([...]) をクリックして **[開く]** ダイアログ ボックスを開き、レポートの処理および式の評価を実行するのに必要なクラスを選択できます。  
  
 **Delete**  
 クラスのインスタンスを削除するには、削除するインスタンスを選択し、 **[削除]** ボタンをクリックします。  
  
 **[上へ]**  
 依存関係のあるクラスについては、この参照の表示位置を一覧の上方に移動できます。  
  
 **[下へ]**  
 依存関係のあるクラスについては、この参照の表示位置を一覧の下方に移動できます。  
  
## <a name="see-also"></a>参照  
 [レポート デザイナーでカスタム コードやアセンブリを式から参照する (SSRS)](report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)   
 [レポート変数コレクションとグループ変数コレクションの参照 (レポート ビルダーおよび SSRS)](report-design/built-in-collections-report-and-group-variables-references-report-builder.md)   
 [式の例 &#40;レポート ビルダーおよび SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md)  
  
  