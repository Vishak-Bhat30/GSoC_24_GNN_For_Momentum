## Model

    MODEL_GNN(
      (conv1): GCNConv(7, 128)
      (conv2): GCNConv(128, 64)
      (conv3): GCNConv(64, 64)
      (conv4): GCNConv(64, 64)
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
