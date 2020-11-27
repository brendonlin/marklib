<template>
  <div>{{ address_tree }}</div>
</template>

<script>
export default {
  name: "MarkWall",
  data() {
    return {
      marks: [
        {
          address: "https://www.google.com/",
          title: "google",
          labels: [],
        },
        {
          address: "https://cn.bing.com/?ensearch=1",
          title: "必应",
          labels: [],
        },
        {
          address: "https://developer.android.google.cn/index.html",
          title: "Android Developers",
          labels: [],
        },
        {
          address:
            "https://developers.google.com/machine-learning/crash-course/ml-intro?hl=zh-cn",
          title:
            "机器学习简介 (Introduction to Machine Learning)  |  机器学习速成课程",
          labels: [],
        },
        {
          address: "http://127.0.0.1:8080",
          title: "本地测试",
          labels: [],
        },
      ],
    };
  },
  methods: {
    add_node: function (parent, child_name) {
      if (!(child_name in parent)) {
        parent[child_name] = {};
      }
      return parent[child_name];
    },
  },
  computed: {
    address_tree() {
      var tree = {};
      const ip_pattern = /^\d+\.\d+\.\d+\.\d+(:\d+)?$/g;
      var domain;
      for (const i in this.marks) {
        const address = new URL(this.marks[i].address);
        const host = address.host;
        if (host.match(ip_pattern)) {
          domain = "IP";
        } else {
          const host_parts = host.split(".");
          domain = host_parts
            .slice(host_parts.length - 2, host_parts.length)
            .join(".");
        }

        // const path = address.pathname;
        // const routes = [domain, host];
        var node;
        node = this.add_node(tree, domain);
        node = this.add_node(node, host);
        this.add_node(node, this.marks[i], true);
        // if (!(domain in tree)) {
        //   tree[domain] = [];
        // } else {
        //   tree[domain].push(host);
        // }
      }
      return tree;
    },
  },
};
</script>

<style lang="scss" scoped>
</style>