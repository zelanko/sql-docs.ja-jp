---
title: '[参照] ([レポートのプロパティ] ダイアログボックス) (レポートビルダー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10082"
ms.assetid: 3414c857-8ea6-4fc4-a6d5-b4883c039efa
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 99fe80a22f380bbe1406d357846c4103eeb0083e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66104393"
---
# <a name="report-properties-dialog-box-references-report-builder"></a>[参照] ([レポートのプロパティ] ダイアログ ボックス) (レポート ビルダー)
  
  **[レポートのプロパティ]** ダイアログ ボックスの **[参照]** を選択すると、レポート定義内の式で使用される、カスタム アセンブリまたは他の外部アセンブリ、およびカスタム クラスのインスタンスへの参照を追加または削除できます。 レポート ビルダーのローカル モードでは、カスタム アセンブリはサポートされません。 カスタムアセンブリを使用するレポートを作成するには[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]、でレポートデザイナーを使用します。  
  
## <a name="options"></a>オプション  
 **[アセンブリの追加または削除]**  
 レポートで参照されるアセンブリを一覧表示します。 アセンブリは、レポートのデザインに使用するツールがインストールされているコンピューターおよびレポート サーバー上で使用できる必要があります。 参照の名前は、レポート定義言語 (.rdl) ファイルの** \<codemodule>** タグの内容と正確に一致する必要があります。  
  
 **追加**  
 アセンブリを追加します。 省略記号ボタン ([...]) をクリックして [**開く**] ダイアログボックスを開き、レポートの処理および式の評価を完了するために必要なアセンブリを選択します。  
  
 **Remove**  
 アセンブリの参照を一覧から削除するには、削除するアセンブリ名を選択し、 **[削除]** ボタンをクリックします。  
  
 **[クラスの追加または削除]**  
 レポートで使用されるクラスのインスタンスを一覧表示します。 クラスの一覧は、静的メンバーではなく、インスタンス ベースのメンバーでのみ使用されます。  
  
 **追加**  
 クラスの参照を追加します。 省略記号ボタン ([...]) をクリックして [**開く**] ダイアログボックスを開き、レポートの処理および式の評価を完了するために必要なクラスを選択します。  
  
 **Remove**  
 クラスのインスタンスを削除するには、削除するインスタンスを選択し、 **[削除]** ボタンをクリックします。  
  
 **Up**  
 依存関係のあるクラスについては、この参照の表示位置を一覧の上方に移動できます。  
  
 **ダウン**  
 依存関係のあるクラスについては、この参照の表示位置を一覧の下方に移動できます。  
  
## <a name="see-also"></a>参照  
 [ダイアログボックス、ペイン、およびウィザードのヘルプのレポートビルダー](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [式 &#40;レポート ビルダーおよび SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md)  
  
  
