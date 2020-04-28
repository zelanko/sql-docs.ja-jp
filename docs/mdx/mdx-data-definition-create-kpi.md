---
title: CREATE KPI ステートメント (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: e2380f72fe8a5faf9dc5504e56941f724b1bd159
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68098397"
---
# <a name="mdx-data-definition---create-kpi"></a>MDX データ操作 - CREATE KPI


  主要業績評価指標 (KPI) を作成します。 KPI は、キューブ内のメジャーグループに関連付けられた計算のコレクションであり、ビジネスまたはシナリオの成功を評価するために使用されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
CREATE KPI CURRENTCUBE | <Cube Name>.KPI_Name AS KPI_Value  
   [,Property_Name = Property_Value, ...n]  
```  
  
## <a name="arguments"></a>引数  
 *KPI_Name*  
 KPI 名を指定する有効な文字列です。  
  
 *KPI_Value*  
 数値を返す有効な多次元式 (MDX) 式です。  
  
 *Property_Name*  
 KPI プロパティの名前を提供する有効な文字列です。  
  
 *Property_Value*  
 KPI のプロパティの値を定義する有効なスカラー式です。  
  
## <a name="remarks"></a>Remarks  
 現在接続されているキューブ以外のキューブを指定すると、エラーが発生します。 したがって、現在のキューブを示すには、キューブ名の代わりに CURRENTCUBE を使用する必要があります。  
  
## <a name="kpi-properties"></a>KPI のプロパティ  
 次の表に、すべての KPI プロパティを示します。 これらのプロパティには既定値がありません。 したがって、KPI のプロパティに特定の値が割り当てられるまで、そのプロパティに対してクエリを実行すると NULL 値が返されます。  
  
|プロパティの識別子|説明|  
|-------------------------|-------------|  
|所得|数値を返す有効な MDX 式です。|  
|状態|数値を返す有効な MDX 式です。|  
|STATUS_GRAPHIC|クライアント アプリケーションが使用するグラフィック イメージのセットを定義する文字列です。|  
|傾向|数値を返す有効な MDX 式です。|  
|TREND_GRAPHIC|クライアント アプリケーションが使用するグラフィック イメージのセットを定義する文字列です。|  
|WEIGHT|数値を返す有効な MDX 式です。|  
|CURRENT_TIME_MEMBER|時間ディメンションのメンバーを返す有効な MDX 式です。 CURRENT_TIME_MEMBER は、すべての相対時間関数の参照ポイントを設定します。|  
|PARENT_KPI|親 KPI の名前を指定する文字列です。|  
|キャプション|KPI のキャプションとしてクライアント アプリケーションが使用する文字列です。|  
|DISPLAY_FOLDER|KPI がクライアントアプリケーションによって表示される、表示フォルダーのパスを指定する文字列。 フォルダー レベルの区切り記号は、クライアント アプリケーションによって定義されます。 によって[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]提供されるツールとクライアントでは\\、円記号 () がレベルの区切り記号です。 定義されたメンバーに複数の表示フォルダーを指定するには、セミコロン (;) を使用します。フォルダーを分離するには|  
|ASSOCIATED_MEASURE_GROUP|すべての MDX 計算で参照される必要がある、メジャー グループの名前を指定する文字列です。|  
  
 [目標]、[状態]、および [傾向] の各プロパティの値は、-1 ~ 1 の範囲で評価される MDX 式です。 ただし、これらのプロパティで実際に使用される値の範囲は、クライアント アプリケーションによって定義されます。 によって[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]提供されるツールとクライアントを使用して kpi を参照する場合、-1 未満の値は-1 として扱われ、1より大きい値は1として扱われます。  
  
 STATUS_GRAPHIC と TREND_GRAPHIC はどちらも、表示するイメージの正しいセットを識別するためにクライアントアプリケーションが使用する文字列値です。 これらの文字列は表示関数の動作も定義します。 この動作には、表示する状態の数 (通常は奇数) と、各状態に使用する画像が含まれます。  
  
### <a name="kpi-graphics-in-sql-server-data-tools"></a>SQL Server Data Tools の KPI グラフィック  
 で[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]は、KPI グラフィックスに3つまたは5つの状態があります。 次の表では、これらの各状態の値を定義します。  
  
|KPI グラフィックの状態の数|これらの状態の値|  
|--------------------------------------|---------------------------|  
|3|Bad =-1 ~-0.5<br /><br /> OK =-0.4999 ~ 0.4999<br /><br /> Good = 0.50 から1|  
|5|悪い = -1 ～ -0.75<br /><br /> リスク =-0.7499 ~-0.25<br /><br /> OK =-0.2499 ~ 0.2499<br /><br /> 上昇 = 0.25 ～ 0.7499<br /><br /> 良い = 0.75 ～ 1|  
  
> [!NOTE]  
>  反転ゲージや反転状態の矢印など、一部のグラフィックでは、範囲が反転されます。 つまり、-1 が良い評価、1 が悪い評価になります。  
  
 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] では、KPI グラフィックの名前によって、そのグラフィックの状態が 3 つであるか 5 つであるかを判断できます。 次の表に、KPI グラフィックスと関連付けられている[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]使用法、名前、および状態の数を示します。  
  
|グラフィックの使用法|KPI グラフィックの名前|状態の数|  
|--------------------|-------------------------|----------------------|  
|状態|図形|3|  
|状態|信号機|3|  
|状態|道路の署名|3|  
|状態|ゲージ|3|  
|状態|反転ゲージ|5|  
|状態|温度計|3|  
|状態|[円柱]|3|  
|状態|顔|3|  
|状態|変位の矢印|3|  
|傾向|標準の矢印|3|  
|傾向|状態の矢印|3|  
|傾向|反転した状態の矢印|5|  
|傾向|顔|3|  
  
## <a name="see-also"></a>参照  
 [MDX&#41;&#40;の KPI ステートメントの削除](../mdx/mdx-data-definition-drop-kpi.md)   
 [Mdx&#41;&#40;mdx データ定義ステートメント](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
