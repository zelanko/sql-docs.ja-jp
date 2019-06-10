---
title: 拡張性 API
titleSuffix: Azure Data Studio
description: Azure Data Studio 機能拡張 Api について説明します
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
manager: jroth
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 3cde890f16e14866238f24e5d8a6bd52efdc9ecc
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66782417"
---
# <a name="azure-data-studio-extensibility-apis"></a>Azure Data Studio 機能拡張 Api

[!INCLUDE[name-sos](../includes/name-sos.md)] 拡張機能は、オブジェクト エクスプ ローラーなどの Azure Data Studio の他の部分との対話に使用できる API を提供します。 これらの Api はから利用可能な[ `src/sql/sqlops.d.ts` ](https://github.com/Microsoft/azuredatastudio/blob/master/src/sql/sqlops.d.ts)ファイルし、以下に示します。

## <a name="connection-management"></a>接続の管理
`sqlops.connection`

### <a name="top-level-functions"></a>最上位の関数

- `getCurrentConnection(): Thenable<sqlops.connection.Connection>` アクティブなエディターまたはオブジェクト エクスプ ローラーの選択に基づいて、現在の接続を取得します。

- `getActiveConnections(): Thenable<sqlops.connection.Connection[]>` アクティブになっているすべてのユーザーの接続の一覧を取得します。 このような接続がない場合は、空のリストを返します。

- `getCredentials(connectionId: string): Thenable<{ [name: string]: string }>` 接続に関連付けられている資格情報を格納しているディクショナリを取得します。 これらは下のオプションのディクショナリの一部として返されるそれ以外の場合、`sqlops.connection.Connection`オブジェクトしますが、そのオブジェクトから取り除かれを取得します。 

### `Connection`
- `options: { [name: string]: string }` 接続オプションの辞書
- `providerName: string` 接続プロバイダーの名前 (例。"MSSQL")
- `connectionId: string` 接続の一意の識別子

### <a name="example-code"></a>コード例
```
> let connection = sqlops.connection.getCurrentConnection();
connection: {
    providerName: 'MSSQL',
    connectionId: 'd97bb63a-466e-4ef0-ab6f-00cd44721dcc',
    options: {
        server: 'mairvine-sql-server',
        user: 'sa',
        authenticationType: 'sqlLogin',
        ...
    },
    ...
}
> let credentials = sqlops.connection.getCredentials(connection.connectionId);
credentials: {
    password: 'abc123'
}

```

## <a name="object-explorer"></a>オブジェクト エクスプローラー

`sqlops.objectexplorer`


### <a name="top-level-functions"></a>最上位の関数
- `getNode(connectionId: string, nodePath?: string): Thenable<sqlops.objectexplorer.ObjectExplorerNode>` 特定の接続とパスに対応するオブジェクト エクスプ ローラーのノードを取得します。 パスが指定されていない場合は、指定された接続の最上位ノードを返します。 返すかどうかのノードがない指定されたパスに、`undefined`します。 注:`nodePath`のオブジェクトは、SQL ツール サービスのバックエンドによって生成され、手動で構築することは困難です。 API の今後の機能強化を使用して、名前、種類、スキーマなど、ノードについて指定したメタデータに基づいてノードを取得するができます。

- `getActiveConnectionNodes(): Thenable<sqlops.objectexplorer.ObjectExplorerNode>` アクティブなすべてのオブジェクト エクスプ ローラー接続ノードを取得します。

- `findNodes(connectionId: string, type: string, schema: string, name: string, database: string, parentObjectNames: string[]): Thenable<sqlops.objectexplorer.ObjectExplorerNode[]>` 指定したメタデータと一致するすべてのオブジェクト エクスプ ローラー ノードを検索します。 `schema`、 `database`、および`parentObjectNames`引数には、`undefined`ときに適用できません。 `parentObjectNames` 目的のオブジェクトであるオブジェクト エクスプ ローラーで最下位のレベルを高いものから、データベース以外の親オブジェクトの一覧を示します。 たとえば、接続の id 列、テーブル"schema1.table1"とデータベース"database1"に属している"column1"を検索するときに`connectionId`、呼び出す`findNodes(connectionId, 'Column', undefined, 'column1', 'database1', ['schema1.table1'])`します。 参照してください、 [Azure Data Studio は既定でサポートされる種類の一覧](https://github.com/Microsoft/azuredatastudio/wiki/Object-Explorer-types-supported-by-FindNodes-API)この API 呼び出し。

### <a name="objectexplorernode"></a>ObjectExplorerNode
- `connectionId: string` 下のノードが存在する接続の id

- `nodePath: string` 呼び出しに使用されるため、ノードのパス、`getNode`関数。

- `nodeType: string` ノードの型を表す文字列

- `nodeSubType: string` ノードのサブタイプを表す文字列

- `nodeStatus: string` ノードの状態を表す文字列

- `label: string` オブジェクト エクスプ ローラーで、ノードのラベルが表示されます。

- `isLeaf: boolean` ノードがリーフ ノードは、子を持たないかどうか

- `metadata: sqlops.ObjectMetadata` このノードによって表されるオブジェクトを記述するメタデータ

- `errorMessage: string` ノードがエラー状態がかどうかに表示されるメッセージ

- `isExpanded(): Thenable<boolean>` オブジェクト エクスプ ローラーでノードが現在展開されているかどうか

- `setExpandedState(expandedState: vscode.TreeItemCollapsibleState): Thenable<void>` ノードを展開または折りたたまれているかどうかを設定します。 状態が [なし] に設定されている場合、ノードは変更されません。

- `setSelected(selected: boolean, clearOtherSelections?: boolean): Thenable<void>` ノードが選択されているかどうかを設定します。 場合`clearOtherSelections`は true、新しい選択を行うときにその他のチェックをオフにします。 False の場合、既存の選択のままにします。 `clearOtherSelections` 既定値は true が`selected`true および false はときに、`selected`は false です。

- `getChildren(): Thenable<sqlops.objectexplorer.ObjectExplorerNode[]>` このノードのノードのすべての子を取得します。 子が存在しない場合は、空のリストを返します。

- `getParent(): Thenable<sqlops.objectexplorer.ObjectExplorerNode>` このノードの親ノードを取得します。 返すには、親が存在しない場合が定義されていません。

### <a name="example-code"></a>コード例

```cs
private async interactWithOENode(selectedNode: sqlops.objectexplorer.ObjectExplorerNode): Promise<void> {
    let choices = ['Expand', 'Collapse', 'Select', 'Select (multi)', 'Deselect', 'Deselect (multi)'];
    if (selectedNode.isLeaf) {
        choices[0] += ' (is leaf)';
        choices[1] += ' (is leaf)';
    } else {
        let expanded = await selectedNode.isExpanded();
        if (expanded) {
            choices[0] += ' (is expanded)';
        } else {
            choices[1] += ' (is collapsed)';
        }
    }
    let parent = await selectedNode.getParent();
    if (parent) {
        choices.push('Get Parent');
    }
    let children = await selectedNode.getChildren();
    children.forEach(child => choices.push(child.label));
    let choice = await vscode.window.showQuickPick(choices);
    let nextNode: sqlops.objectexplorer.ObjectExplorerNode = undefined;
    if (choice === choices[0]) {
        selectedNode.setExpandedState(vscode.TreeItemCollapsibleState.Expanded);
    } else if (choice === choices[1]) {
        selectedNode.setExpandedState(vscode.TreeItemCollapsibleState.Collapsed);
    } else if (choice === choices[2]) {
        selectedNode.setSelected(true);
    } else if (choice === choices[3]) {
        selectedNode.setSelected(true, false);
    } else if (choice === choices[4]) {
        selectedNode.setSelected(false);
    } else if (choice === choices[5]) {
        selectedNode.setSelected(false, true);
    } else if (choice === 'Get Parent') {
        nextNode = parent;
    } else {
        let childNode = children.find(child => child.label === choice);
        nextNode = childNode;
    }
    if (nextNode) {
        let updatedNode = await sqlops.objectexplorer.getNode(nextNode.connectionId, nextNode.nodePath);
        this.interactWithOENode(updatedNode);
    }
}

vscode.commands.registerCommand('mssql.objectexplorer.interact', () => {
    sqlops.objectexplorer.getActiveConnectionNodes().then(activeConnections => {
        vscode.window.showQuickPick(activeConnections.map(connection => connection.label + ' ' + connection.connectionId)).then(selection => {
            let selectedNode = activeConnections.find(connection => connection.label + ' ' + connection.connectionId === selection);
            this.interactWithOENode(selectedNode);
        });
    });
});
```

## <a name="proposed-apis"></a>提案された Api

ダイアログ ボックス、ウィザード、およびその他の機能の間でのドキュメント タブにカスタム UI を表示する拡張機能を許可する提案された Api が追加されました。 参照してください、[提案されている API の種類のファイル](https://github.com/Microsoft/azuredatastudio/blob/master/src/sql/sqlops.proposed.d.ts)詳細なドキュメントについては、ただしするこれらの API は、いつでも変更されることに注意してください。 これらの Api の一部を使用する方法の例が記載されて、 ["sql サービス"の拡張機能サンプル](https://github.com/Microsoft/azuredatastudio/tree/master/samples/sqlservices)します。


