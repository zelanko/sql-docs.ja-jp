---
title: OPENQUERY (DMX) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- OPENQUERY
dev_langs:
- DMX
helpviewer_keywords:
- OPENQUERY statement
ms.assetid: fe57f3a3-a8e6-402c-995e-bd2fe28a7a7c
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 6e8c250b96c2da83e6dd34263ccddeb622a67050
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="ltsource-data-querygt---openquery"></a>&lt;ソース データ クエリ&gt;-OPENQUERY
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  ソース データ クエリを既存のデータ ソースへのクエリで置き換えます。 INSERT、SELECT FROM PREDICTION JOIN、および SELECT FROM NATURAL PREDICTION JOIN ステートメントをサポートして**OPENQUERY**です。  
  
## <a name="syntax"></a>構文  
  
```  
  
OPENQUERY(<named datasource>, <query syntax>)  
```  
  
## <a name="arguments"></a>引数  
 *名前付きのデータ ソース*  
 上に存在するデータ ソース、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]データベース。  
  
 *クエリ構文*  
 行セットを返すクエリ構文です。  
  
## <a name="remarks"></a>解説  
 **OPENQUERY**データ ソースの権限をサポートすることによって外部データにアクセスするより安全な方法を提供します。 接続文字列はデータ ソースに格納されるので、管理者はデータ ソースのプロパティを使用して、データへのアクセスを管理することができます。 データ ソースの詳細については、次を参照してください。[データ ソースのサポートと #40 です。SSAS - 多次元 &#41;](../analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional.md).  
  
 クエリを実行して、サーバーで使用できるデータ ソースの一覧を取得できる、 **MDSCHEMA_INPUT_DATASOURCES**スキーマ行セット。 使用しての詳細については**MDSCHEMA_INPUT_DATASOURCES**を参照してください[MDSCHEMA_INPUT_DATASOURCES 行セット](../analysis-services/schema-rowsets/ole-db-olap/mdschema-input-datasources-rowset.md)です。  
  
 また、次の DMX クエリを使用すると、現在の Analysis Services データベース内のデータ ソースの一覧を返すこともできます。  
  
 `SELECT * FROM $system.MDSCHEMA_INPUT_DATASOURCES`  
  
## <a name="examples"></a>使用例  
 次の例で既に定義されている MyDS データ ソースを使用して、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]への接続を作成するデータベース、[!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]データベースとクエリ、 **vTargetMail**ビュー。  
  
```  
OPENQUERY (MyDS,'SELECT TOP 1000 * FROM vTargetMail')  
```  
  
## <a name="see-also"></a>参照  
 [&#60;以外の場合はソース データ クエリ &#62;。](../dmx/source-data-query.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;データ操作ステートメント](../dmx/dmx-statements-data-manipulation.md)   
 [データ マイニング拡張機能 &#40;DMX&#41; ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
