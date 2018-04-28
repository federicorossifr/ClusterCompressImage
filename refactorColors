function [original,modified,cl_index,cl_center] = refactorColors(filename,numColors)
    im = imread(filename);
    sizes = size(im);
    im_x = sizes(1);
    im_y = sizes(2);
    iml1 = im(:,:,1);
    iml2 = im(:,:,2);
    iml3 = im(:,:,3);
    scatter3(iml1(:),iml2(:),iml3(:),1);
    xlabel("R");
    ylabel("G");
    zlabel("B");
    hold on;
    pixels = double([iml1(:) iml2(:) iml3(:)]);
    [cl_index,cl_center] = kmeans(double(pixels),numColors);
    scatter3(cl_center(:,1),cl_center(:,2),cl_center(:,3),'filled','black');
    imout = zeros(im_x*im_y,3);
    for i=1:im_x*im_y
       imout(i,:) = round(cl_center(cl_index(i),:));
    end
    imout = round(imout);
    modified = uint8(reshape(imout,[im_x,im_y,3]));
    ml1 = modified(:,:,1);
    ml2 = modified(:,:,2);
    ml3 = modified(:,:,3);
    scatter3(ml1(:),ml2(:),ml3(:),10,'yellow');
    legend("Original","Centroids","Compressed");    
    original = im;
end

