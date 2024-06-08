## The model architecture

    MODEL_GNN(
      (conv1): GCNConv(7, 128)
      (conv2): GATConv(128, 64, heads=1)
      (conv3): GATConv(64, 64, heads=1)
      (conv4): SAGEConv(64, 64, aggr=mean)
      (lin1): Linear(in_features=128, out_features=128, bias=True)
      (lin2): Linear(in_features=128, out_features=16, bias=True)
      (lin3): Linear(in_features=16, out_features=16, bias=True)
      (lin4): Linear(in_features=16, out_features=1, bias=True)
      (lin5): Linear(in_features=128, out_features=128, bias=True)
      (lin6): Linear(in_features=128, out_features=16, bias=True)
      (lin7): Linear(in_features=16, out_features=16, bias=True)
      (lin8): Linear(in_features=16, out_features=1, bias=True)
      (global_att_pool1): GlobalAttention(gate_nn=Sequential(
        (0): Linear(in_features=64, out_features=1, bias=True)
      ), nn=None)
      (global_att_pool2): GlobalAttention(gate_nn=Sequential(
        (0): Linear(in_features=64, out_features=1, bias=True)
      ), nn=None)
    )

## Training HyperParamters


criterion- 

y_t = $(y_true<80).type(torch.FloatTensor)*y_true.type(torch.FloatTensor)$ + 
$(y_true>=80).type(torch.FloatTensor)*(y_true<250).type(torch.FloatTensor)*y_true.type(torch.FloatTensor)**2.4$ + $(y_true>=160).type(torch.FloatTensor)*10$

`return torch.mean(y_t.type(torch.FloatTensor)*torch.pow((y_pred-y_true)/y_true,2).type(torch.FloatTensor))/250`
