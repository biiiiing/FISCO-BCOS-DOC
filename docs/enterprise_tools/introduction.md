# 基本介绍

## 设计背景

现有的联盟链运维管理工具在初始化时都没有考虑联盟链间多个企业地位对等的诉求。联盟链在初始化时，需要协商创世节点中包含的节点信息。因此谁来生成这些信息就显得十分重要。现有做法为某一机构生成自己的节点信息，启动区块链，再加入其它机构的节点；或是由权威第三方机构直接生成所有机构内的节点信息，并将安装包发送给各机构。

FISCO BCOS 2.0引入了隐私性和可扩展性更强的多群组架构。群组架构易用性更强，使得企业建链像建微信群一样便利；在群组架构下，群组间数据、交易相互隔离，每个群组运行独立的共识算法，可满足区块链场景中的隐私保护需求。

如何保证企业间如何对等、安全、隐私地新建群组。新建群组之后如何保证节点可靠，有效的运行；群组账本的隐私性和安全性，以及企业建立群组、使用群组操作的隐私性都需要一个有效的方式来保证。

- 传统工具在部署时没有考虑节点私钥的安全性，以及机构间对等、去中心化的部署联盟链的诉求。

- 传统方案缺少一种企业间对等、隐私协商多群组联盟链中新群组建立、划分的方式。

## 设计思路

fisco generator从上述背景出发，根据灵活、安全、易用、对等的原则，从不同机构对等部署、新建群组的角度考虑，设计了解决上述问题的解决方案。

针对同一根证书的联盟链，本工具可以快速配置链内的多个群组，满足不同企业的不同业务需求。

![](../../images/enterprise/feature.png)

使用时，不同机构间通过协商节点证书、ip、端口号等数据的模式，填写配置项，每个机构都可以在本地生成不含节点私钥的安装包。使用这种方式，在保证节点可用的同时，保护节点的安全性。

使用时，本工具会根据用户配置的配置文件（包含节点的hostip，端口号等信息），及meta目录下用户存放的符合命名规范的节点证书，生成节点所需启动的安装包。

用户生成安装包后，导入私钥，启动节点，节点会根据用户配置信息进行多群组组网。

<!-- ## 业务示例

以多群组使用中常见的星型拓扑结构为例。在这种业务模式中，联盟链的某一个或几个机构节点会处于多个群组账本中，其他节点分别处于不同的群组中。

针对于传统联盟链方案而言，假设机构A维护上述星型拓扑结构的中心节点，则假设有n个账本时，机构A需要至少部署n个节点，才能与所有其他节点进行交互。采用FISCO BCOS 2.0的多群组架构，机构A只需要维护一个节点，通过为节点配置多个群组，即可完成上述需求。

示意图如下图所示：

![](../..//images/enterprise/simple_star1.png)

组网步骤如下：

1. 所有节点根据所处群组分别采用链下安全方式交换证书，如节点0需要与其他所有节点交换证书，节点2只需要和节点0交换证书
2. 使用生成节点安装包（可以采用某一个机构生成全部安装包并分发给其他人，也可以各自机构生成自己的安装包）
3. 不同机构将节点私钥导入到对应节点安装包文件夹下
4. 推送节点安装包至对应服务器
5. 启动节点

至此，完成了如图所示的星型模式组网。

更多组网示例模式及具体操作，请参考[场景分析](./playgroud/index.html)。 -->