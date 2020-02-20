---
title: 手順 1:Node.js 開発用に開発環境を構成する | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 2dad01f1-fadf-4ac9-9b4d-26be3d301886
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bce89cc12c7493522de55adffb69fcbe3307cbdf
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "68003764"
---
# <a name="step-1--configure-development-environment-for-nodejs-development"></a>手順 1:Node.js 開発用に開発環境を構成する
SQL Server 用の Node.js ドライバーを使用してアプリケーションを開発するには、前提条件を使用して開発環境を構成する必要があります。  最も一般的な方法は、ノード パッケージ マネージャー (npm) を使用して面倒なモジュールをインストールすることですが、必要に応じて [Github](https://github.com/pekim/tedious) で面倒なモジュールを直接ダウンロードすることもできます。  
  
Node.js ドライバーでは TDS プロトコルが使用されていることに注意してください。これは SQL Server と Azure SQL Database で既定で有効になっています。  追加の構成は不要です。  
  
## <a name="windows"></a>Windows  
  
1. **Node.js ランタイムと npm パッケージ マネージャーをインストールします**  
a. [Node.js](https://nodejs.org/en/download/) にアクセスします  
b. 適切な Windows インストーラーの msi リンクをクリックします   
c. ダウンロードが完了したら、msi を実行して Node.js をインストールします  
  
2. **cmd.exe を開きます**  
  
3. **プロジェクト ディレクトリを作成**し、それに移動します。    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
4. **ノード プロジェクトを作成します。**  プロジェクトの作成時に既定値を保持するには、プロジェクトが作成されるまで Enter キーを押します。 この手順の最後に、プロジェクト ディレクトリに package.json ファイルが表示されます。  
```  
> npm init  
```  
  
5. **tedious モジュールをプロジェクトにインストールします。**  これは、ドライバーが SQL Server と通信するために使用する TDS プロトコルの実装です。  
```  
> npm install tedious  
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1.  **ターミナルを開きます**  
  
2. **Node.js ランタイムをインストールします**  
```  
>sudo apt-get install node  
```  
3. **npm (ノード パッケージ マネージャー) をインストールします**  
```  
> sudo apt-get install npm  
```  
4. **プロジェクト ディレクトリを作成**し、それに移動します。    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
  
5. **ノード プロジェクトを作成します。**  プロジェクトの作成時に既定値を保持するには、プロジェクトが作成されるまで Enter キーを押します。 この手順の最後に、プロジェクト ディレクトリに package.json ファイルが表示されます。  
```  
> sudo npm init  
```  
  
6. **tedious モジュールをプロジェクトにインストールします。**  これは、ドライバーが SQL Server と通信するために使用する TDS プロトコルの実装です。  
```  
> sudo npm install tedious  
```  
  
## <a name="mac"></a>Mac  
  
1. **Node.js ランタイムと npm パッケージ マネージャーをインストールします**  
a. [Node.js](https://nodejs.org/en/download/) にアクセスします  
b. 適切な Mac OS インストーラーのリンクをクリックします。  
c. ダウンロードが完了したら、dmg を実行して Node.js をインストールします  
  
2. **ターミナルを開きます**  
  
3. **プロジェクト ディレクトリを作成**し、それに移動します。    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
  
4. **ノード プロジェクトを作成します。**  プロジェクトの作成時に既定値を保持するには、プロジェクトが作成されるまで Enter キーを押します。 この手順の最後に、プロジェクト ディレクトリに package.json ファイルが表示されます。  
```  
> npm init  
```  
  
5. **tedious モジュールをプロジェクトにインストールします。**  これは、ドライバーが SQL Server と通信するために使用する TDS プロトコルの実装です。  
```  
> npm install tedious  
```  
  
