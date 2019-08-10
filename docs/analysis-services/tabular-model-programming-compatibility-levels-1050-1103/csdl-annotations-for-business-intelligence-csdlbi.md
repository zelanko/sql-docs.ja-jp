---
title: ビジネスインテリジェンスの CSDL 注釈 (CSDLBI) |Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 23a7433ffb0f06330c948de0955193a885eec768
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68890183"
---
# <a name="csdl-annotations-for-business-intelligence-csdlbi"></a>ビジネス インテリジェンス向けの CSDL 注釈 (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、ビジネス インテリジェンス注釈付き概念スキーマ定義言語 (CSDLBI) と呼ばれる XML 形式でのテーブル モデルの定義の表示をサポートします。 このトピックでは、CSDLBI の概要および [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データ モデルでの使用方法について説明します。  
  
## <a name="understanding-the-role-of-csdl"></a>CSDL の役割について  
 概念スキーマ定義言語 (CSDL) は、エンティティ、リレーションシップ、および関数を記述する XML ベースの言語です。 CSDL は Entity Data Framework の一部として定義されます。 BI 注釈は、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] を使用してデータ モデリングをサポートするための拡張機能です。  
  
 CSDL は Entity Data Framework に準拠していますが、エンティティとリレーションシップのモデルについての理解や、テーブル モデルまたはモデルに基づくレポートを構築するための専用ツールは必要ありません。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] などのクライアント ツールや AMO などの API を使用してモデルを作成し、それをサーバーに配置します。  
  
 CSDLBI スキーマは、[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] などのクライアントからのモデル定義の要求に対して、Analysis Services サーバーで生成されます。 クライアント アプリケーションは、モデル データをホストする Analysis Services サーバーに XML クエリを送信します。 その応答として、サーバーはモデル内のエンティティの定義を含む XML メッセージを CSDLBI 注釈を使用して送信します。 レポートクライアントは、この情報を使用して、モデルで使用できるフィールド、集計、およびメジャーを表示します。 CSDLBI 注釈は、データのグループ化、並べ替え、および書式設定の方法に関する情報も提供します。  
  
 CSDLBI の一般的な情報については、「 [CSDLBI の概念](https://docs.microsoft.com/bi-reference/csdl/csdlbi-concepts)」を参照してください。  
  
### <a name="working-with-csdl"></a>CSDL の操作  
 特定のテーブル モデルを表す CSDLBI 注釈のセットは、単純型と複合型の両方のエンティティのコレクションを含む XML ドキュメントです。 エンティティは、計算列、メジャーまたは KPI に含まれるテーブル (またはディメンション)、列 (属性)、関連付け (リレーションシップ) および式を定義します。  
  
 これらのオブジェクトを直接変更することはできません。テーブル モデルを操作するには、クライアント ツールおよびアプリケーション プログラミング インターフェイス (API) を使用してください。  
  
 モデルの CSDL を取得するには、モデルをホストするサーバーに DISCOVER 要求を送信します。 この要求は、サーバーとモデルのほか、必要に応じてビューまたはパースペクティブを指定して修飾する必要があります。 返されるメッセージは、XML 文字列です。 一部の要素は言語に依存しているため、現在の接続の言語に応じて異なる値が返される可能性があります。 詳細については、「 [DISCOVER_CSDL_METADATA Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-csdl-metadata-rowset)」を参照してください。  
  
### <a name="csdlbi-versions"></a>CSDLBI のバージョン  
 元の CSDL 仕様 (Entity Data Framework に基づく) では、モデリングのサポートに必要なエンティティとプロパティの大半が規定されています。 BI 注釈は、テーブル モデルの特殊な要件、[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] などのクライアントに必要なレポート プロパティ、および多次元モデルに必要な追加のメタデータをサポートします。 このセクションでは、各バージョンでの更新内容を説明します。  
  
 **CSDLBI 1.0**  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] テーブル モデルをサポートするために CSDL スキーマに追加された最初のセットです。データ モデリング、カスタム計算、および拡張表現をサポートする注釈を含みました。  
  
-   テーブル モデルをサポートする新しい要素とプロパティ。 たとえば、モデルの作成に使用されるデータベース クエリの種類を指定するためのプロパティが追加されました。  
  
-   既存のエンティティの新しいプロパティと拡張。  たとえば、リレーションシップをサポートするように Association 要素が拡張されました。  
  
-   視覚化プロパティとナビゲーション プロパティ。 たとえば、カスタムの並べ替えフィールド、既定の画像をサポートするためのプロパティが追加されました。  
  
 **CSDLBI 1.1**  
  
 このバージョンの CSDLBI スキーマは、多次元データベース (OLAP キューブなど) をサポートします。 新しい要素とプロパティは次のとおりです。  
  
-   エンティティとしてディメンションのサポート。  
  
-   階層のサポート。  
  
-   ROLAP パーティションの公開。  
  
-   翻訳のサポート  
  
-   パースペクティブのサポート。  
  
 CSDLBI 注釈の個々の要素の詳細については、「 [CSDL への BI 注釈のテクニカルリファレンス](https://docs.microsoft.com/bi-reference/csdl/technical-reference-for-bi-annotations-to-csdl)」を参照してください。 CSDL のコア仕様の詳細については、MSDN の[csdl の仕様](http://go.microsoft.com/fwlink/?LinkId=205855)を参照してください。  
  
## <a name="see-also"></a>参照  
 [互換性レベル1050から1103までの表形式オブジェクトモデルについて](https://docs.microsoft.com/analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103)   
 [CSDLBI の概念](https://docs.microsoft.com/bi-reference/csdl/csdlbi-concepts)   
 [互換性レベル1050から1103までの表形式オブジェクトモデルについて](https://docs.microsoft.com/analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103)  
  
  
