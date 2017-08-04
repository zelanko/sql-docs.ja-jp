---
title: "スクリプト変換エディター (スクリプト ページ) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.scriptcomponent.script.f1
helpviewer_keywords:
- Script Transformation Editor
ms.assetid: 4c6d1901-ef21-4aa7-9d0a-6bbeb7fadf1c
caps.latest.revision: 38
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ce227c91ad8109f3f8f7686e01a219392146602e
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="script-transformation-editor-script-page"></a>[スクリプト変換エディター] ([スクリプト] ページ)
  **[スクリプト変換エディター]** ダイアログ ボックスの **[スクリプト]** タブを使用すると、スクリプトおよび関連プロパティを指定できます。  
  
 スクリプト コンポーネントの詳細については、「 [Script Component](../../../integration-services/data-flow/transformations/script-component.md) 」および「 [Configuring the Script Component in the Script Component Editor](../../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)」を参照してください。 スクリプト コンポーネントのプログラミングの詳細については、「 [Extending the Data Flow with the Script Component](../../../integration-services/extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **プロパティ**  
 スクリプト変換のプロパティを表示および変更します。 表示されるプロパティの多くは読み取り専用です。 以下のプロパティを変更できます。  
  
|値|Description|  
|-----------|-----------------|  
|**Description**|スクリプト変換の目的を記述します。|  
|**LocaleID**|ロケールを指定して、順序付けおよび日時の変換に関する地域固有の情報を提供します。|  
|**名前**|わかりやすいコンポーネント名を入力します。|  
|**[ValidateExternalMetadata]**|スクリプト変換において、デザイン時に外部データ ソースに対して列のメタデータを検証するかどうかを示します。 値 **false** を設定した場合、検証は実行時まで延期されます。|  
|**[ReadOnlyVariables]**|スクリプト変換が読み取り専用でアクセスする変数の、コンマ区切りの一覧を入力します。<br /><br /> 注: 変数名では大文字と小文字が区別されます。|  
|**[ReadWriteVariables]**|スクリプト変換が読み取り/書き込み用にアクセスする変数の、コンマ区切りの一覧を入力します。<br /><br /> 注: 変数名では大文字と小文字が区別されます。|  
|**[ScriptLanguage]**|スクリプト コンポーネントが使用するスクリプト言語を選択します。<br /><br /> スクリプト コンポーネントとスクリプト タスクの既定のスクリプト言語を設定するには、 **[オプション]** ダイアログ ボックスの **[全般]** ページにある **[スクリプト言語]** オプションを使用します。|  
|**[UserComponentTypeName]**|指定します、<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponentHost>クラスおよび**Microsoft.SqlServer.TxScript**をサポートするアセンブリ、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]インフラストラクチャです。|  
  
 **[スクリプトの編集]**  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) を使用して、スクリプトを作成または変更します。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../../integration-services/integration-services-error-and-message-reference.md)   
 [スクリプト コンポーネントの種類を選択します。](../../../integration-services/data-flow/transformations/select-script-component-type.md)   
 [[スクリプト変換エディター] &#40;[入力列] ページ&#41;](../../../integration-services/data-flow/transformations/script-transformation-editor-input-columns-page.md)   
 [スクリプト変換エディターと &#40; 入力および呼び出し力 ページ、&#41; です。](../../../integration-services/data-flow/transformations/script-transformation-editor-inputs-and-outputs-page.md)   
 [スクリプト変換エディターと &#40; です。接続マネージャー ページと &#41; です。](../../../integration-services/data-flow/transformations/script-transformation-editor-connection-managers-page.md)   
 [その他のスクリプト コンポーネントの例](../../../integration-services/extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)  
  
  
