---
title: '[スクリプト変換エディター] ([スクリプト] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scriptcomponent.script.f1
helpviewer_keywords:
- Script Transformation Editor
ms.assetid: 4c6d1901-ef21-4aa7-9d0a-6bbeb7fadf1c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 31dc7fca17ea5e00a242e8c32fb2a3514c5e7732
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85422209"
---
# <a name="script-transformation-editor-script-page"></a>[スクリプト変換エディター] ([スクリプト] ページ)
  **[スクリプト変換エディター]** ダイアログ ボックスの **[スクリプト]** タブを使用すると、スクリプトおよび関連プロパティを指定できます。  
  
 スクリプト コンポーネントの詳細については、「 [Script Component](data-flow/transformations/script-component.md) 」および「 [Configuring the Script Component in the Script Component Editor](extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)」を参照してください。 スクリプト コンポーネントのプログラミングの詳細については、「 [スクリプト コンポーネントによるデータ フローの拡張](extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **プロパティ**  
 スクリプト変換のプロパティを表示および変更します。 表示されるプロパティの多くは読み取り専用です。 以下のプロパティを変更できます。  
  
|[値]|説明|  
|-----------|-----------------|  
|**説明**|スクリプト変換の目的を記述します。|  
|**ロケール**|ロケールを指定して、順序付けおよび日時の変換に関する地域固有の情報を提供します。|  
|**名前**|わかりやすいコンポーネント名を入力します。|  
|**[ValidateExternalMetadata]**|スクリプト変換において、デザイン時に外部データ ソースに対して列のメタデータを検証するかどうかを示します。 値 `false` を設定した場合、検証は実行時まで延期されます。|  
|**[ReadOnlyVariables]**|スクリプト変換が読み取り専用でアクセスする変数の、コンマ区切りの一覧を入力します。<br /><br /> 注: 変数名では大文字と小文字が区別されます。|  
|**[ReadWriteVariables]**|スクリプト変換が読み取り/書き込み用にアクセスする変数の、コンマ区切りの一覧を入力します。<br /><br /> 注: 変数名では大文字と小文字が区別されます。|  
|**[ScriptLanguage]**|スクリプト コンポーネントが使用するスクリプト言語を選択します。<br /><br /> スクリプトコンポーネントとスクリプトタスクの既定のスクリプト言語を設定するには、[**オプション**] ダイアログボックスの **[全般**] ページにある [**スクリプト言語**] オプションを使用します。 詳細については、「 [General Page](general-page-of-integration-services-designers-options.md)」を参照してください。|  
|**[UserComponentTypeName]**|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インフラストラクチャをサポートする <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponentHost> クラスおよび `Microsoft.SqlServer.TxScript` アセンブリを指定します。|  
  
 **[スクリプトの編集]**  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tools for APPLICATIONS (VSTA) を使用して、スクリプトを作成または変更します。  
  
## <a name="see-also"></a>関連項目  
 [Integration Services のエラーとメッセージの参照](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [スクリプトコンポーネントの種類を選択](../../2014/integration-services/select-script-component-type.md)   
 [[スクリプト変換エディター] &#40;[入力列] ページ&#41;](../../2014/integration-services/script-transformation-editor-input-columns-page.md)   
 [[スクリプト変換エディター] の [入力および出力] ページ &#40;&#41;](../../2014/integration-services/script-transformation-editor-inputs-and-outputs-page.md)   
 [[スクリプト変換エディター] &#40;[接続マネージャー] ページ&#41;](../../2014/integration-services/script-transformation-editor-connection-managers-page.md)   
 [その他のスクリプト コンポーネントの例](extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)  
  
  
