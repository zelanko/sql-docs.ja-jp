---
title: スクリプト変換エディター ([スクリプト] ページ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scriptcomponent.script.f1
helpviewer_keywords:
- Script Transformation Editor
ms.assetid: 4c6d1901-ef21-4aa7-9d0a-6bbeb7fadf1c
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 102988ac347543a4d2e2110d4c8511c398be9348
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48060682"
---
# <a name="script-transformation-editor-script-page"></a>[スクリプト変換エディター] ([スクリプト] ページ)
  **[スクリプト変換エディター]** ダイアログ ボックスの **[スクリプト]** タブを使用すると、スクリプトおよび関連プロパティを指定できます。  
  
 スクリプト コンポーネントの詳細については、「 [Script Component](data-flow/transformations/script-component.md) 」および「 [Configuring the Script Component in the Script Component Editor](extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)」を参照してください。 スクリプト コンポーネントのプログラミングの詳細については、「 [Extending the Data Flow with the Script Component](extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md)」を参照してください。  
  
## <a name="options"></a>および  
 **[プロパティ]**  
 スクリプト変換のプロパティを表示および変更します。 表示されるプロパティの多くは読み取り専用です。 以下のプロパティを変更できます。  
  
|ReplTest1|Description|  
|-----------|-----------------|  
|**[説明]**|スクリプト変換の目的を記述します。|  
|**LocaleID**|ロケールを指定して、順序付けおよび日時の変換に関する地域固有の情報を提供します。|  
|**名前**|わかりやすいコンポーネント名を入力します。|  
|**[ValidateExternalMetadata]**|スクリプト変換において、デザイン時に外部データ ソースに対して列のメタデータを検証するかどうかを示します。 値`false`の実行時まで検証が遅延します。|  
|**[ReadOnlyVariables]**|スクリプト変換が読み取り専用でアクセスする変数の、コンマ区切りの一覧を入力します。<br /><br /> 注: 変数名では大文字と小文字が区別されます。|  
|**[ReadWriteVariables]**|スクリプト変換が読み取り/書き込み用にアクセスする変数の、コンマ区切りの一覧を入力します。<br /><br /> 注: 変数名では大文字と小文字が区別されます。|  
|**[ScriptLanguage]**|スクリプト コンポーネントが使用するスクリプト言語を選択します。<br /><br /> スクリプト コンポーネントとスクリプト タスクの既定のスクリプト言語を設定するには、 **[オプション]** ダイアログ ボックスの **[全般]** ページにある **[スクリプト言語]** オプションを使用します。 詳細については、「 [General Page](general-page-of-integration-services-designers-options.md)」を参照してください。|  
|**[UserComponentTypeName]**|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インフラストラクチャをサポートする <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponentHost> クラスおよび `Microsoft.SqlServer.TxScript` アセンブリを指定します。|  
  
 **[スクリプトの編集]**  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tools for Applications (VSTA) を使用して、スクリプトを作成または変更します。  
  
## <a name="see-also"></a>関連項目  
 [Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [スクリプト コンポーネントの種類を選択します。](../../2014/integration-services/select-script-component-type.md)   
 [スクリプト変換エディター&#40;入力列 ページ&#41;](../../2014/integration-services/script-transformation-editor-input-columns-page.md)   
 [スクリプト変換エディター&#40;入力し、出力のページ&#41;](../../2014/integration-services/script-transformation-editor-inputs-and-outputs-page.md)   
 [スクリプト変換エディター&#40;接続マネージャー ページ&#41;](../../2014/integration-services/script-transformation-editor-connection-managers-page.md)   
 [その他のスクリプト コンポーネントの例](extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)  
  
  
