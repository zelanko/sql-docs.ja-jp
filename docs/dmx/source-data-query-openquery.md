---
title: OPENQUERY (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 1079fbb02026e2043767082d5def7fac37322ef2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68077729"
---
# <a name="ltsource-data-querygt---openquery"></a>&lt;ソース データ クエリ&gt;-OPENQUERY
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  ソース データ クエリを既存のデータ ソースへのクエリで置き換えます。 INSERT、SELECT FROM PREDICTION JOIN、および SELECT FROM NATURAL PREDICTION JOIN ステートメントをサポートして**OPENQUERY**します。  
  
## <a name="syntax"></a>構文  
  
```  
  
OPENQUERY(<named datasource>, <query syntax>)  
```  
  
## <a name="arguments"></a>引数  
 *名前付きのデータ ソース*  
 上に存在するデータ ソース、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]データベース。  
  
 *クエリ構文*  
 行セットを返すクエリ構文です。  
  
## <a name="remarks"></a>コメント  
 **OPENQUERY**データ ソースのアクセス許可をサポートすることによって外部データにアクセスするより安全な方法を提供します。 接続文字列はデータ ソースに格納されるので、管理者はデータ ソースのプロパティを使用して、データへのアクセスを管理することができます。 データ ソースの詳細については、次を参照してください。[サポートされるデータ ソース&#40;SSAS - 多次元&#41;](../analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional.md)します。  
  
 クエリを実行して、サーバーで使用できるデータ ソースの一覧を取得することができます、 **MDSCHEMA_INPUT_DATASOURCES**スキーマ行セット。 使用しての詳細については**MDSCHEMA_INPUT_DATASOURCES**を参照してください[MDSCHEMA_INPUT_DATASOURCES 行セット](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-input-datasources-rowset)します。  
  
 また、次の DMX クエリを使用すると、現在の Analysis Services データベース内のデータ ソースの一覧を返すこともできます。  
  
 `SELECT * FROM $system.MDSCHEMA_INPUT_DATASOURCES`  
  
## <a name="examples"></a>使用例  
 次の例で既に定義されている MyDS データ ソースを使用して、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]への接続を作成するデータベース、[!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]データベースとクエリ、 **vTargetMail**ビュー。  
  
```  
OPENQUERY (MyDS,'SELECT TOP 1000 * FROM vTargetMail')  
```  
  
## <a name="see-also"></a>参照  
 [&#60;ソース データ クエリ&#62;](../dmx/source-data-query.md)   
 [データ マイニング拡張機能&#40;DMX&#41;データ操作ステートメント](../dmx/dmx-statements-data-manipulation.md)   
 [データ マイニング拡張機能 &#40;DMX&#41; ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
