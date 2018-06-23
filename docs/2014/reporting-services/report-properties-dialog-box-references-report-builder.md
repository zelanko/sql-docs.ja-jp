---
title: レポートのプロパティ ダイアログ ボックスの参照 (レポート ビルダー) |Microsoft ドキュメント
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
- "10082"
ms.assetid: 3414c857-8ea6-4fc4-a6d5-b4883c039efa
caps.latest.revision: 11
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: a33b1456e31220a2453cf318cf3d925c1002260f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36164723"
---
# <a name="report-properties-dialog-box-references-report-builder"></a>[参照] ([レポートのプロパティ] ダイアログ ボックス) (レポート ビルダー)
  **[レポートのプロパティ]** ダイアログ ボックスの **[参照]** を選択すると、レポート定義内の式で使用される、カスタム アセンブリまたは他の外部アセンブリ、およびカスタム クラスのインスタンスへの参照を追加または削除できます。 レポート ビルダーのローカル モードでは、カスタム アセンブリはサポートされません。 レポートを作成するカスタム アセンブリを使用して、レポート デザイナーを使用する[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]です。  
  
## <a name="options"></a>および  
 **追加またはアセンブリを削除します。**  
 レポートで参照されるアセンブリを一覧表示します。 アセンブリは、レポートのデザインに使用するツールがインストールされているコンピューターおよびレポート サーバー上で使用できる必要があります。 参照の名前がの内容と一致する必要があります **\<CodeModule >** レポート定義言語 (.rdl) ファイル内にタグを正確にします。  
  
 **[追加]**  
 アセンブリを追加します。 参照ボタン ([...]) をクリックして **[開く]** ダイアログ ボックスを開き、レポートの処理および式の評価を実行するのに必要なアセンブリを選択します。  
  
 **削除**  
 アセンブリの参照を一覧から削除するには、削除するアセンブリ名を選択し、 **[削除]** ボタンをクリックします。  
  
 **追加または削除するクラス**  
 レポートで使用されるクラスのインスタンスを一覧表示します。 クラスの一覧は、静的メンバーではなく、インスタンス ベースのメンバーでのみ使用されます。  
  
 **[追加]**  
 クラスの参照を追加します。 参照ボタン ([...]) をクリックして **[開く]** ダイアログ ボックスを開き、レポートの処理および式の評価を実行するのに必要なクラスを選択できます。  
  
 **削除**  
 クラスのインスタンスを削除するには、削除するインスタンスを選択し、 **[削除]** ボタンをクリックします。  
  
 **[上へ]**  
 依存関係のあるクラスについては、この参照の表示位置を一覧の上方に移動できます。  
  
 **[下へ]**  
 依存関係のあるクラスについては、この参照の表示位置を一覧の下方に移動できます。  
  
## <a name="see-also"></a>参照  
 [レポート ビルダーのダイアログ ボックス、ペイン、およびウィザードに関するヘルプ](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [式 &#40;レポート ビルダーおよび SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md)  
  
  