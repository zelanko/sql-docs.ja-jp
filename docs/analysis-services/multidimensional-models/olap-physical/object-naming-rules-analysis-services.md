---
title: "オブジェクトの名前付け規則 (Analysis Services) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords: objects [Analysis Services], naming
ms.assetid: b338a60d-4802-4b68-862a-6dc6a3f75e48
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 1493d5236d4c44fe4a496a67a2c435aab703daa8
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="object-naming-rules-analysis-services"></a>オブジェクトの名前付け規則 (Analysis Services)
  このトピックでは、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のコードまたはスクリプトにおけるオブジェクトの名前付け規則、および、オブジェクト名で使用できない予約語と文字について説明します。  
  
##  <a name="bkmk_Names"></a>名前付け規則  
 すべてのオブジェクトが、**名前**と**ID**プロパティを親コレクションのスコープ内で一意である必要があります。 たとえば、所属するデータベースが異なっていれば、2 つのディメンションが同じ名前であってもかまいません。  
  
 手動で指定できますが、 **ID**は通常自動生成されたオブジェクトを作成します。 変更しないで、 **ID**モデルの構築を開始した後です。 モデル内のすべてのオブジェクト参照がに基づいて、 **ID**です。 したがって、変更、 **ID**モデルの破損を招くことが容易にします。  
  
 **DataSource**と**DataSourceView**オブジェクトが名前付け規則に注目すべき例外を設定します。 **DataSource** ID は、現在のデータベースへの参照として、一意ではない 1 つのドット (.) に設定することができます。 次の例外は**DataSourceView**、に対して定義されている名前付け規則に準拠する**データセット**、.NET Framework 内のオブジェクトを**名前**として使用される、識別子です。  
  
 次の規則を適用する**名前**と**ID**プロパティです。  
  
-   名前では大文字と小文字は区別されません。 同じデータベース内に "sales" および "Sales" という 2 つの Cube が存在することはできません。  
  
-   オブジェクト名の先頭または末尾にスペースを付けることは許されません。ただし名前の途中にスペースを入れることはできます。 先頭および末尾にあるスペースは暗黙的に切り捨てられます。 両方に適用、**名前**と**ID**のオブジェクト。  
  
-   最大文字数は 100 文字です。  
  
-   識別子の最初の文字に関する特別な要件はありません。 最初の文字は、有効な文字を使用できます。  
  
##  <a name="bkmk_reserved"></a>予約語と文字  
 予約語は英語で、オブジェクト名に適用されます。キャプションには適用されません。 不注意で予約語をオブジェクト名に使用すると、検証エラーが発生します。 多次元モデルとデータ マイニング モデルでは、どのような場合でも、以下で説明する予約語をオブジェクト名で使用することはできません。  
  
 テーブル モデルでは、データベース互換性が 1103 に設定されている場合、一部のオブジェクトで検証ルールが緩められており、一部のクライアント アプリケーションの拡張文字要件と名前付け規則のためにルールに準拠していません。 これらの条件を満たすデータベースは、厳格でない検証ルールに従います。 この場合、制限された文字がオブジェクト名に使用されていても、検証に合格することがあります。  
  
 **予約語**  
  
-   AUX  
  
-   CLOCK$  
  
-   COM1 ～ COM9 (COM1、COM2、COM3 など)  
  
-   CON  
  
-   LPT1 ～ LPT9 (LPT1、LPT2、LPT3 など)  
  
-   NUL (NUL)  
  
-   PRN  
  
-   NULL は XML 内の文字列の文字として許容されません。   
  
 **予約文字**  
  
 次の表では、特定のオブジェクトで無効な文字を示します。  
  
|オブジェクト|無効な文字|  
|------------|------------------------|  
|**[サーバー]**|サーバー オブジェクトに名前を付けるときは、Windows サーバーの名前付け規則に従います。 参照してください[名前付け規則 (Windows)](http://msdn.microsoft.com/library/windows/desktop/ms682856\(v=vs.85\).aspx)詳細についてはします。|  
|**DataSource**|: / \ * &#124; ? " () [] {} &lt;&gt;|  
|**レベル**または**属性**|のインスタンスにアクセスするたびに SQL Server ログインを指定する必要はありません。 , ; ' ` : / \ * &#124; ? " & % $ ! + = [] {} < >|  
|**ディメンション**または**階層**|のインスタンスにアクセスするたびに SQL Server ログインを指定する必要はありません。 , ; ' ` : / \ * &#124; ? " & % $ ! + = () [] {} \<,>|  
|他のすべてのオブジェクト|のインスタンスにアクセスするたびに SQL Server ログインを指定する必要はありません。 , ; ' ` : / \ * &#124; ? " & % $ ! + = () [] {} < >|  
  
 **例外処理: 場合の予約された文字が許可されます。**  
  
 先に述べたように、特定のモダリティと互換性レベルを持つデータベースでは、予約文字を含むオブジェクト名を使用できます。 拡張文字を使用できる表形式データベース (1103 以上) の場合、ディメンション属性、階層、レベル、メジャー、および KPI オブジェクト名で予約文字を使用できます。  
  
|サーバー モードとデータベース互換性レベル|予約文字を使用できるか|  
|--------------------------------------------------|----------------------------------|  
|MOLAP (すべてのバージョン)|不可|  
|表形式の 1050|不可|  
|表形式 - 1100|不可|  
|表形式 – 1130 以上|可|  
  
 データベースは既定の ModelType を持つことができます。 既定値は多次元モデルと同等です。そのため、列名での予約文字の使用はサポートされません。  
  
## <a name="see-also"></a>参照  
 [MDX の予約語](../../../mdx/mdx-reserved-words.md)   
 [Analysis Services での翻訳のサポート](../../../analysis-services/translation-support-in-analysis-services.md)   
 [XML for Analysis への準拠と #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-for-analysis-compliance-xmla.md)  
  
  
