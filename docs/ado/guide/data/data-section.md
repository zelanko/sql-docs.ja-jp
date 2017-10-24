---
title: "データ セクション |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data section [ADO]
ms.assetid: 43dc42a8-7057-48e6-93d6-880d5c5c51a4
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 62eb026fac4588cc159afec1714a6aa51903aa8a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="data-section"></a>データ セクション
データ セクションでは、更新、挿入、または削除保留中のいずれかと共に、行セットのデータを定義します。 データ セクションには、0 個以上の行を含めることができます。 行が、スキーマで定義されている 1 つの行セットからのデータだけを含めることができます。 また、前述したとおり、データを含まない列は省略できます。 データ セクションの属性またはサブ要素が使用され、スキーマ」セクションでその構造体が定義されていない場合は、サイレント モードで無視されます。  
  
## <a name="string"></a>文字列  
 予約済みの XML 文字テキスト データでは、適切な文字エン ティティに置き換える必要があります。 たとえば、会社名「Joe ガレージ」では、単一引用符置き換える必要がありますのエンティティによってです。 実際の行は、次のようにします。  
  
```  
<z:row CompanyName="Joe's Garage"/>  
```  
  
 次の文字は XML に予約されていると、文字エンティティで置き換える必要があります: {'、"、&、\<、>} です。  
  
## <a name="binary"></a>Binary  
 バイナリ データは、マップされる bin.hex エンコード (つまり、2 つの文字にマップを 1 バイト、ニブルあたり 1 つの文字) です。  
  
## <a name="datetime"></a>DateTime  
 バリアントの VT_DATE 形式が XML データのデータ型によって直接サポートされていません。 データと時刻の両方のコンポーネントを含む日付の正しい形式は、yyyy、mm-ddThh:mm:ss です。  
  
 XML で指定された日付形式に関する詳細については、次を参照してください。、 [W3C の XML データの指定](https://go.microsoft.com/fwlink/?LinkId=5692)です。  
  
 XML データの指定が 2 つの同等のデータ型を定義する場合 (たとえば、i4 int を = =)、ADO はフレンドリ名を書き込みますが、読み取りは両方。  
  
## <a name="managing-pending-changes"></a>保留中の変更を管理します。  
 レコード セットは、イミディ エイトで開くことまたはバッチ更新モードです。 クライアント側のカーソルをバッチ更新モードで開かれたときに、レコード セットに加えられたすべての変更は、保留中状態 UpdateBatch メソッドが呼び出されるまでです。 保留中の変更も永続化レコード セットを保存するとします。 XML では、これらが urn: スキーマで定義されている「更新」要素を使用して表されます。-microsoft-com:rowset です。 さらに、行セットを更新できる場合、更新可能なプロパティ必要がありますに設定する行の定義では true です。 たとえば、ある Shippers テーブルには、保留中の変更が含まれています、行の定義は定義する外観のようになります次です。  
  
```  
<s:ElementType name="row" content="eltOnly" updatable="true">  
  <s:attribute type="ShipperID"/>  
  <s:attribute type="CompanyName"/>  
  <s:attribute type="Phone"/>  
  <s:extends type="rs:rowbase"/>  
</s:ElementType>  
```  
  
 これにより、ADO は更新可能なレコード セット オブジェクトを構築できるように、画面のデータを永続化プロバイダーが示しています。  
  
 次のサンプル データは、挿入、変更、および削除を永続化されたファイルで検索する方法を示しています。  
  
```  
<rs:data>  
  <z:row ShipperID="2" CompanyName="United Package"   
    Phone="(503) 555-3199"/>  
<rs:update>  
  <rs:original>  
    <z:row ShipperID="3" CompanyName="Federal Shipping"   
      Phone="(503) 555-9931"/>  
  </rs:original>  
  <z:row Phone="(503) 552-7134"/>  
</rs:update>  
<rs:insert>  
  <z:row ShipperID="12" CompanyName="Lightning Shipping"   
    Phone="(505) 111-2222"/>  
  <z:row ShipperID="13" CompanyName="Thunder Overnight"   
    Phone="(505) 111-2222"/>  
  <z:row ShipperID="14" CompanyName="Blue Angel Air Delivery"   
    Phone="(505) 111-2222"/>  
</rs:insert>  
<rs:delete>  
  <z:row ShipperID="1" CompanyName="Speedy Express" Phone="(503) 555-9831"/>  
</rs:delete>  
</rs:data>  
```  
  
 更新プログラムには、常に変更された行のデータが続きます全体の元の行データが含まれています。 変更された行は、すべての列または実際に変更された列のみに含まれている可能性があります。 前の例で出荷業者の 2 行は変更されず、Phone 列だけ Shipper 3 の値が変更された、変更された行に含まれる唯一の列であるためです。 Shippers 12、13、および 14 の挿入された行は、バッチ化 rs: 挿入の 1 つのタグです。 これは、前の例では表示されませんが、削除された行もバッチ処理できる同時に、注意してください。  
  
## <a name="see-also"></a>参照  
 [XML 形式で保持するレコード](../../../ado/guide/data/persisting-records-in-xml-format.md)

