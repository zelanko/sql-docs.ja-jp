---
title: "レコードおよびフィールドのプロバイダーが指定した |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- records-provided fields [ADO]
- provider-supplied fields [ADO]
ms.assetid: 77f95e0a-0cf2-411a-a792-593f77330fbd
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 93b97bce2562604a01c564a376bd093abb9b1b7c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="records-and-provider-supplied-fields"></a>レコードとプロバイダーが指定したフィールド
ときに、[レコード](../../../ado/reference/ado-api/record-object-ado.md)オブジェクトを開くと、そのソースは、開いているは、現在の行を指定できます[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)、絶対 URL または相対 URL、開いていると組み合わせて[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクト.  
  
 場合、**レコード**から開かれた、 **Recordset**、**レコード**オブジェクト[フィールド](../../../ado/reference/ado-api/fields-collection-ado.md)コレクションは、のすべてのフィールドを含める**レコード セット**、さらに、基になるプロバイダーによって追加されたすべてのフィールドです。  
  
 プロバイダーの補助特性として機能する追加のフィールドを挿入、**レコード**です。 その結果、**レコード**ではなく一意のフィールドを持つことがあります、 **Recordset**全体またはそのいずれかとして**レコード**の別の行から派生した、 **Recordset**.  
  
 すべての行など、 **Recordset**データ ソースがこのようなからとして、列がある可能性があり、サブジェクト電子メールから派生します。 A**レコード**そこから派生した**Recordset**同じフィールドになります。 ただし、**レコード**によって表される特定のメッセージに固有の他のフィールドがあります**レコード**、添付ファイルや Cc (carbon copy) などです。  
  
 **レコード**オブジェクトとの現在の行、 **Recordset** 、同じフィールドを持つが異なるため**レコード**と**Recordset**オブジェクトは、さまざまなメソッドとプロパティがあります。  
  
 保持している共通のフィールド、**レコード**と**Recordset**いずれかのオブジェクトに変更することができます。 ただし、フィールドを削除できません、**レコード**オブジェクトを基になるプロバイダーが、フィールドを null に設定をサポートします。  
  
 後に、**レコード**が開くと、プログラムでフィールドを追加できます。 追加すると、フィールドを削除することもできますが、元のフィールドを削除することはできません、 **Recordset**です。  
  
 開くことも、**レコード**からオブジェクトを直接 URL です。 ここでは、フィールドに追加、**レコード**基になるプロバイダーに依存します。 現時点では、ほとんどのプロバイダーがで表されるエンティティを記述するフィールドのセットを追加、**レコード**です。 エンティティがの場合は、単純なファイルなどのバイト ストリーム、[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)通常からオブジェクトを開くことができます、**レコード**です。  
  
## <a name="special-fields-for-document-source-providers"></a>ドキュメントの特別なフィールドのソース プロバイダー  
 特殊なクラスと呼ばれる、プロバイダーの*ドキュメントのソース プロバイダー*フォルダーを管理、およびドキュメントします。 ときに、**レコード**ドキュメントやオブジェクトを表す**Recordset**オブジェクトは、ドキュメントのフォルダーを表し、ドキュメントのソース プロバイダーは、それらのオブジェクトを記述するフィールドの一意のセットを作成ドキュメントの特性代わりに、実際のドキュメント自体にします。 通常、1 つのフィールドへの参照が含まれます。、**ストリーム**のドキュメントを表すです。  
  
 これらのフィールドを構成して、リソース**レコード**または**recordset**でそれらをサポートする特定のプロバイダーの一覧表示と[付録 a: プロバイダー](../../../ado/guide/appendixes/appendix-a-providers.md)です。  
  
 2 つの定数のインデックス、**フィールド**リソースのコレクション**レコード**または**Recordset**をよく使用されるフィールドのペアを取得します。 **フィールド**オブジェクト[値](../../../ado/reference/ado-api/value-property-ado.md)プロパティは、目的のコンテンツを返します。  
  
-   アクセスされるフィールド、 **adDefaultStream**定数に関連付けられている既定のストリームが含まれています、**レコード**または**Recordset**オブジェクト。 プロバイダーは、既定のストリームをオブジェクトに割り当てます。  
  
-   アクセスされるフィールド、 **adRecordURL**定数には、ドキュメントを識別する絶対 URL が含まれています。  
  
 ドキュメントのソース プロバイダーがサポートしていません、[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)のコレクション**レコード**と**フィールド**オブジェクト。 内容、**プロパティ**コレクションがこのようなオブジェクトに対して null です。  
  
 ドキュメントのソース プロバイダーがなど、プロバイダー固有のプロパティを追加する場合があります**データソースの種類**をドキュメントのソース プロバイダーであるかどうかを識別します。 プロバイダーの種類を決定する方法の詳細については、プロバイダーのマニュアルを参照してください。  
  
## <a name="resource-recordset-columns"></a>リソース レコード セットの列  
 A*リソース レコード セット*次の列で構成されています。  
  
|列名|型|Description|  
|-----------------|----------|-----------------|  
|RESOURCE_PARSENAME|AdVarWChar|読み取り専用です。 リソースの URL を示します。|  
|RESOURCE_PARENTNAME|AdVarWChar|読み取り専用です。 親レコードの絶対 URL を示します。|  
|RESOURCE_ABSOLUTEPARSENAME|AdVarWChar|読み取り専用です。 PARENTNAME と PARSENAME の連結は、リソースの絶対 URL を示します。|  
|RESOURCE_ISHIDDEN|adBoolean|リソースが表示されていない場合は true。 行セットを明示的に作成するコマンドが RESOURCE_ISHIDDEN が True である行を選択しない限り、行は返されません。|  
|RESOURCE_ISREADONLY|adBoolean|リソースが読み取り専用である場合は true。 開こうとして DBBINDFLAG_WRITE し、このリソースは、DB_E_READONLY で失敗します。 読み取り専用リソースで開かれた場合でも、このプロパティを編集することができます。|  
|RESOURCE_CONTENTTYPE|AdVarWChar|ドキュメントの使用方法を示す — たとえば、弁護士の簡単なです。 これは、ドキュメントの作成に使用された Office テンプレートに対応して可能性があります。|  
|RESOURCE_CONTENTCLASS|AdVarWChar|などの形式を示す、ドキュメントの MIME の種類を示す"`text/html`"です。|  
|RESOURCE_CONTENTLANGUAGE|AdVarWChar|コンテンツが格納されている言語を示します。|  
|RESOURCE_CREATIONTIME|adFileTime|読み取り専用です。 FILETIME 構造体、リソースが作成された時刻を含んでいることを示します。 時刻は協定世界時 (UTC) 形式で報告されます。|  
|RESOURCE_LASTACCESSTIME|adFileTime|読み取り専用です。 FILETIME 構造体、リソースの最終アクセス時刻が含まれることを示します。 時刻は UTC 形式です。 FILETIME メンバーは、プロバイダーがこの時間メンバーをサポートしていない場合に 0 をします。|  
|RESOURCE_LASTWRITETIME|adFileTime|読み取り専用です。 FILETIME 構造体、リソースが最後に書き込まれた時刻を含んでいることを示します。 時刻は UTC 形式です。 FILETIME メンバーは、プロバイダーがこの時間メンバーをサポートしていない場合に 0 をします。|  
|RESOURCE_STREAMSIZE|asUnsignedBigInt|読み取り専用です。 (バイト単位) のリソースの既定のストリームのサイズを示します。|  
|RESOURCE_ISCOLLECTION|adBoolean|読み取り専用です。 リソースがディレクトリなど、コレクションの場合は true。 リソースが単純なファイルである場合は false です。|  
|RESOURCE_ISSTRUCTUREDDOCUMENT|adBoolean|リソースが構造化ドキュメントの場合は true。 False の場合は、リソースは、構造化ドキュメントではありません。 コレクションまたは単純なファイルがある可能性があります。|  
|DEFAULT_DOCUMENT|AdVarWChar|読み取り専用です。 このリソースに、フォルダーの既定の単純なドキュメントまたは構造化ドキュメントの URL が含まれていることを示します。 既定のストリームが、そのリソースから要求されたときに使用されます。 このプロパティは、単純なファイルの場合は空白です。|  
|CHAPTERED_CHILDREN|AdChapter|読み取り専用です。 省略可。 リソースの子を含む行セットのチャプターを示します。 (、 *OLE DB Provider for Internet Publishing*この列は使用しません)。|  
|RESOURCE_DISPLAYNAME|AdVarWChar|読み取り専用です。 リソースの表示名を示します。|  
|RESOURCE_ISROOT|adBoolean|読み取り専用です。 リソースがコレクションまたは構造化ドキュメントのルートである場合は true。|  
  
## <a name="see-also"></a>参照  
 [Record オブジェクト (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [付録 a: プロバイダー](../../../ado/guide/appendixes/appendix-a-providers.md)

