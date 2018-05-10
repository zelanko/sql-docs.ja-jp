---
title: 多次元モデル内のアクション |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 03d7e3fd90aeb130988eb79d1c9849043f5d56f1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="actions-in-multidimensional-models"></a>多次元モデルのアクション
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  アクションは、選択したキューブまたはキューブの一部でエンド ユーザーが行う操作です。 この操作では、選択されているアイテムをパラメーターとして設定してアプリケーションを起動したり、選択されているアイテムに関する情報を取得したりすることができます。 アクションの詳細については、「[アクション &#40;Analysis Services - 多次元データ&#41;](../../analysis-services/multidimensional-models/actions-analysis-services-multidimensional-data.md)」を参照してください。  
  
 キューブのアクションを作成するには、キューブ デザイナーの **[アクション]** タブを使用します。 次の指定を行います。  
  
 **名前**  
 アクションを識別する名前を選択します。  
  
 **[アクションの対象]**  
 アクションをアタッチするオブジェクトを選択します。 一般に、クライアント アプリケーションでは、エンド ユーザーが対象オブジェクトを選択するとアクションが表示されます。ただし、クライアント アプリケーションは、どのエンド ユーザーの操作でアクションを表示するかを決定します。 **[対象になる種類]** には、次のいずれかのオブジェクトを選択します。  
  
-   [属性メンバー]  
  
-   [セル]  
  
-   Cube  
  
-   [ディメンションのメンバー]  
  
-   階層  
  
-   [階層メンバー]  
  
-   レベル  
  
-   [レベル メンバー]  
  
 対象になるオブジェクトの種類を選択したら、指定した種類のキューブ オブジェクトを **[対象になるオブジェクト]** から選択します。  
  
 **[条件 (省略可能)]**  
 ブール値に解決される多次元式 (MDX) を指定します。省略可能です。 値が **True**の場合、アクションは指定された対象オブジェクトに対して実行されます。 値が **False**の場合、アクションは実行されません。  
  
 **[アクションの内容]**  
 アクションの種類を選択します。 次の表は、使用できる種類をまとめたものです。  
  
|型|Description|  
|----------|-----------------|  
|[データ セット]|データセットを取得します。|  
|[専用]|この一覧に表示されていないインターフェイスを使用して操作を実行します。|  
|[行セット]|行セットを取得します。|  
|ステートメントから削除してください。|OLE DB コマンドを実行します。|  
|[URL]|インターネット ブラウザーで変数ページを表示します。|  
  
 **[アクションの式]** に、アクションが実行されたときに渡されるパラメーターを指定します。 構文の評価結果は文字列型になる必要があり、MDX で記述した式を含める必要があります。 たとえば、MDX 式では、構文に含まれるキューブの一部を指定できます。 MDX 式が評価されてから、パラメーターが渡されます。 また、MDX ビルダーを使用すると、MDX 式を作成できます。  
  
 **[追加のプロパティ]**  
 プロパティを選択します。 次の表は、使用できるプロパティをまとめたものです。  
  
|プロパティ|Description|  
|--------------|-----------------|  
|**[呼び出し]**|アクションを実行する方法を指定します。 既定の [インタラクティブ] を指定すると、アクションはユーザーがオブジェクトにアクセスしたときに実行されます。 次の設定が可能です。<br /><br /> [バッチ]<br /><br /> Interactive<br /><br /> [オープン時]|  
|**アプリケーション**|アクションのアプリケーションについて説明します。|  
|**Description**|アクションについて説明します。|  
|**Caption**|アクションに関して表示されるキャプションを指定します。 キャプションが MDX の場合は、 **[キャプションに MDX を使用]** に **True**を指定します。|  
|**True**|キャプションが MDX の場合は **True** 、MDX でない場合は **False** を指定します。|  
  
> [!NOTE]  
>  HTML およびコマンド ラインのアクションの種類を定義するには、Analysis Services スクリプト言語 (ASSL) または分析管理オブジェクト (AMO) を使用する必要があります。 詳細については、「[アクション要素 &#40;ASSL&#41;](../../analysis-services/scripting/objects/action-element-assl.md)」「[Type 要素 &#40;アクション&#41; &#40;ASSL&#41;](../../analysis-services/scripting/properties/type-element-action-assl.md)」、および「[高度な AMO OLAP オブジェクトのプログラミング](../../analysis-services/multidimensional-models/analysis-management-objects/programming-amo-olap-advanced-objects.md)」を参照してください。  
  
## <a name="creating-a-reporting-action"></a>レポート アクションの作成  
 レポート サーバーは、レポートに関する URL ベースの要求に応答します。 レポート アクションを作成するには、 **[キューブ]** メニューの **[新しいレポート アクション]** をクリックします。 次のオプションは、レポート アクションに固有です。  
  
 **レポート サーバー**  
 次の表で説明するプロパティは、レポート サーバーに対して指定されます。  
  
|プロパティ|Description|  
|--------------|-----------------|  
|**サーバー名**|サポート サーバーを稼働しているコンピューターの名前です。|  
|**[サーバー パス]**|レポート サーバーによって公開されたパスです。|  
|**[レポート形式]**|HTML5、HTML3、Excel、または PDF です。|  
  
> [!NOTE]  
>  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]では、サーバー名プロパティに Transport Layer Security (https:) を指定できます。  
  
 **[パラメーター (省略可能)]**  
 パラメーターは、アクションが作成されると、URL 文字列の一部としてサーバーに送信されます。 パラメーターには、 **[パラメーター名]** と、MDX 式である **[パラメーター値]** が含まれます。  
  
 レポート サーバーの URL は、次のように構成されます。  
  
```  
  
http://  
host  
/  
virtualdirectory  
/Path&  
parametername1  
=  
parametervalue1  
& ...  
```  
  
 以下に例を示します。  
  
```  
http://localhost/ReportServer/Sales/YearlySalesByCategory?rs:Command=Render&Region=West  
```  
  
## <a name="creating-a-drillthrough-action"></a>ドリルスルー アクションの作成  
 ドリルスルー アクションは、クライアント アプリケーションにドリルスルー ステートメントとして返される行セット アクションによって定義されます。 アクションの対象は、メジャー グループのメンバーです。 新しいドリルスルー アクションを作成するには、 **[キューブ]** メニューの **[新しいドリルスルー アクション]** をクリックします。 次のオプションは、ドリルスルー アクションに固有です。  
  
 **[ドリルスルー列]**  
 1 つまたは複数のディメンションと、アクションによってクライアント アプリケーションに返されるドリルスルー列をディメンションごとに選択します。  
  
## <a name="see-also"></a>参照  
 [多次元モデルのキューブ](../../analysis-services/multidimensional-models/cubes-in-multidimensional-models.md)  
  
  
