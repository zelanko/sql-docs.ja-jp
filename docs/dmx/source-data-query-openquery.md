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
ms.openlocfilehash: caac43eb176e17a6e92e487f3dedae71a252f5af
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68887728"
---
# <a name="ltsource-data-querygt---openquery"></a>&lt;ソースデータクエリ&gt; -OPENQUERY
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  クエリを使用してソースデータクエリを既存のデータソースに置き換えます。 INSERT、SELECT FROM 予測結合、および SELECT FROM ナチュラル予測結合ステートメントでは、 **OPENQUERY**がサポートされています。  
  
## <a name="syntax"></a>構文  
  
```  
  
OPENQUERY(<named datasource>, <query syntax>)  
```  
  
## <a name="arguments"></a>引数  
 *名前付きデータソース*  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]データベースに[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]存在するデータソース。  
  
 *クエリ構文*  
 行セットを返すクエリ構文です。  
  
## <a name="remarks"></a>解説  
 **OPENQUERY**は、データソースのアクセス許可をサポートすることにより、外部データにアクセスするより安全な方法を提供します。 接続文字列はデータソースに格納されるため、管理者はデータソースのプロパティを使用してデータへのアクセスを管理できます。 データソースの詳細については、「[サポートされるデータソース &#40;SSAS-多次元&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional)」を参照してください。  
  
 サーバーで使用できるデータソースの一覧を取得するには、 **MDSCHEMA_INPUT_DATASOURCES**スキーマ行セットに対してクエリを実行します。 **MDSCHEMA_INPUT_DATASOURCES**の使用方法の詳細については、「 [MDSCHEMA_INPUT_DATASOURCES 行セット](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-input-datasources-rowset)」を参照してください。  
  
 次の DMX クエリを使用して、現在の Analysis Services データベースのデータソースの一覧を返すこともできます。  
  
 `SELECT * FROM $system.MDSCHEMA_INPUT_DATASOURCES`  
  
## <a name="examples"></a>例  
 次の例では、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]データベースに既に定義されている myds データソースを[!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]使用して、データベースへの接続を作成し、 **vtargetmail**ビューに対してクエリを実行します。  
  
```  
OPENQUERY (MyDS,'SELECT TOP 1000 * FROM vTargetMail')  
```  
  
## <a name="see-also"></a>参照  
 [&#60;ソースデータクエリ&#62;](../dmx/source-data-query.md)   
 [DMX&#41; データ操作ステートメントを &#40;データマイニング拡張機能](../dmx/dmx-statements-data-manipulation.md)   
 [DMX&#41; ステートメントリファレンス &#40;データマイニング拡張機能](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
