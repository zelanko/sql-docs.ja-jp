---
title: Microsoft Visual Basic と ADO を使用して |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- ADO, Visual Basic
- Visual Basic [ADO]
ms.assetid: 9dfb6784-037d-4f9d-bb7f-b506b4498573
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0250faf780229ec06c5fce38997bbf4eaf51cc43
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35271301"
---
# <a name="using-ado-with-microsoft-visual-basic-and-visual-basic-for-applications"></a>アプリケーションの Microsoft Visual Basic および Visual Basic と ADO の併用
ADO プロジェクトの設定や ADO コードの記述はのようなアプリケーションの Visual Basic または Visual Basic を使用するかどうかです。 このトピックでは、Visual Basic および Visual Basic の両方で ADO を使用してアプリケーションに対応し、ノートのすべての差異。

## <a name="referencing-the-ado-library"></a>ADO ライブラリを参照します。
 ADO ライブラリは、プロジェクトによって参照される必要があります。

#### <a name="to-reference-ado-from-microsoft-visual-basic"></a>Microsoft Visual Basic から ADO を参照するには

1.  Visual basic での**プロジェクト**メニューの **参照しています.**.

2.  選択**Microsoft ActiveX Data Objects x.x ライブラリ**一覧からです。 以上であることを確認も次のライブラリが選択されます。

    -   Visual Basic for Applications

    -   Visual Basic ランタイム オブジェクトとプロシージャ

    -   Visual Basic のオブジェクトとプロシージャ

    -   OLE オートメーション

3.  **[OK]** をクリックします。

 ADO を使用でき同じくらい簡単に Visual Basic によるアプリケーションについては、たとえば Microsoft Access を使用して、します。

#### <a name="to-reference-ado-from-microsoft-access"></a>Microsoft Access から ADO を参照するには

1.  Microsoft Access で選択するかのモジュールを作成、**モジュール** タブで、**データベース**ウィンドウです。

2.  **ツール**メニューの **参照しています.**.

3.  選択**Microsoft ActiveX Data Objects x.x ライブラリ**一覧からです。 以上であることを確認も次のライブラリが選択されます。

    -   Visual Basic for Applications

    -   Microsoft Access 8.0 オブジェクト ライブラリ (またはそれ以降)

    -   DAO 3.5 オブジェクト ライブラリ (またはそれ以降)

4.  **[OK]** をクリックします。

## <a name="creating-ado-objects-in-visual-basic"></a>Visual Basic では ADO オブジェクトの作成
 オートメーション変数とその変数にオブジェクトのインスタンスを作成するには、2 つのメソッドを使用することができます: **Dim**または**CreateObject**です。

### <a name="dim"></a>Dim
 使用することができます、**新規**キーワード**Dim**宣言され、1 つの手順で ADO オブジェクトのインスタンスを作成します。

```
Dim conn As New ADODB.Connection
```

 または、 **Dim**ステートメントの宣言とオブジェクトのインスタンス化は、次の 2 つの手順を実行することもできます。

```
Dim conn As ADODB.Connection
Set conn = New ADODB.Connection
```

> [!NOTE]
>  明示的に使用する必要はありません、`ADODB`と progid、 **Dim**ステートメントでは、正しくプロジェクトで、ADO ライブラリを参照するいると仮定するとします。 ただし、使用することにより、する必要があるない名前の他のライブラリと競合します。

> [!NOTE]
>  たとえば、同じプロジェクトでは ADO および DAO の両方への参照を含める場合は、インスタンス化するときに使用するには、どのオブジェクト モデルを指定する修飾子を含める必要があります**Recordset**オブジェクトは、次のコードのようにします。

```
Dim adoRS As ADODB.Recordset
Dim daoRS As DAO.Recordset
```

### <a name="createobject"></a>CreateObject
 **CreateObject**メソッド宣言、オブジェクトのインスタンス化は 2 つの段階である必要があります。

```
Dim conn1
Set conn1 = CreateObject("ADODB.Connection") As Object
```

 オブジェクトがインスタンス化される**CreateObject**遅延バインディングがない厳密に型指定し、コマンド ライン入力候補が無効になっていることを意味します。 ただし、では、プロジェクトから ADO ライブラリの参照をスキップすることし、特定のバージョンのオブジェクトをインスタンス化することができます。 以下に例を示します。

```
Set conn1 = CreateObject("ADODB.Connection.2.0") As Object
```

 具体的には、ADO バージョン 2.0 のタイプ ライブラリへの参照を作成し、オブジェクトを作成するこの実現することもできます。

 使用してオブジェクトをインスタンス化する、 **CreateObject**メソッドは一般に使用するよりも低速、 **Dim**ステートメントです。

## <a name="handling-events"></a>イベントを処理
 Microsoft Visual Basic での ADO イベントを処理するために、モジュール レベル変数を使用してを宣言する必要があります、 **WithEvents**キーワード。 変数は、クラス モジュールの一部としてのみ宣言することができ、モジュール レベルで宣言する必要があります。 ADO イベント処理の詳細については、次を参照してください。 [ADO イベントを処理](../../../ado/guide/data/handling-ado-events.md)です。

## <a name="visual-basic-examples"></a>Visual Basic の例
 多くの Visual Basic の例は、ADO のドキュメントに含まれています。 詳細については、次を参照してください。 [ADO コードの例では、Microsoft Visual Basic](../../../ado/reference/ado-api/ado-code-examples-in-visual-basic.md)です。

## <a name="see-also"></a>参照
 [Microsoft ActiveX Data Objects (ADO)](../../../ado/microsoft-activex-data-objects-ado.md) [Microsoft Visual C で ADO を使用して](../../../ado/guide/appendixes/using-ado-with-microsoft-visual-c.md)[スクリプト言語と ADO の併用](../../../ado/guide/appendixes/using-ado-with-scripting-languages.md)
